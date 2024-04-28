---
title: Go 1.23 Timer Channel Changes
---

Go 1.23 includes a new implementation of the channel-based timers
created by [time.NewTimer](/pkg/time/#NewTimer), [time.After](/pkg/time/#After),
[time.NewTicker](/pkg/time/#NewTicker), and [time.Tick](/pkg/time/#Tick).

The new implementation makes two important changes:

 1. Unstopped timers and tickers that are no longer referenced can be garbage collected.
    Before Go 1.23, unstopped timers could not be garbage collected until the timer went off,
    and unstopped tickers could never be garbage collected.
    The Go 1.23 implementation avoids resource leaks in programs that don't use `t.Stop`.

 2. Timer channels are now synchronous (unbuffered), giving the `t.Reset` and `t.Stop`
    methods a stronger guarantee: after one of those methods returns, no future receive from the
    timer channel will observe a stale time value corresponding to the old timer
    configuration. Before Go 1.23, it was impossible to avoid stale values with `t.Reset`,
    and avoiding stale values with `t.Stop` required careful use of the return value from `t.Stop`.
    The Go 1.23 implementation removes this concern entirely.

The implementation changes have two observable side effects that may affect production
behavior or tests, described in the following sections.

The new implementation is only used in programs where package main is in a module
with a `go.mod` declaring `go 1.23` or later.
Other programs continue to use the old semantics.
The [GODEBUG setting](/doc/godebug) `asynctimerchan=1` forces the old semantics;
conversely, `asynctimerchan=0` forces the new semantics.

## Cap and Len

Before Go 1.23, the `cap` of a timer channel was 1, and the `len` of a timer channel
indicated whether a value was waiting to be received (1 if so, 0 if not).
The Go 1.23 implementation creates timer channels with `cap` and `len` always 0.

In general, using `len` to poll any channel is usually not helpful, since another goroutine may
receive from the channel concurrently, invalidating the result of `len` at any time.
Code that polls a timer channel using `len` should instead use a non-blocking select.

That is, code that does:

	if len(t.C) == 1 {
		<-t.C
		more code
	}

should instead do:

	select {
	default:
	case <-t.C:
		more code
	}

## Select Races

Before Go 1.23, a timer created with a very short interval, like 0ns or 1ns,
would take significantly longer than that interval to make its channel ready
for receiving, due to scheduling delays. That delay can be observed
in code that selects between a channel that is ready before the select
and a newly created timer with a very short timeout:

	c := make(chan bool)
	close(c)

	select {
	case <-c:
		println("done")
	case <-time.After(1*time.Nanosecond):
		println("timeout")
	}

By the time the select arguments are evaluated and select looks at
the channels involved, the timer should have expired, meaning
that both cases are ready to proceed. Select chooses between multiple
ready cases by choosing one randomly, so this program should
select each case about half the time.

Due to the scheduling delays in the timer implementation before Go 1.23,
programs like this incorrectly executed the “done” case 100% of the time.

The Go 1.23 timer implementation is not affected by the same scheduling delays,
so in Go 1.23, that program executes each case about half the time.

During testing of Go 1.23 in Google's code base, we found a handful of tests
that used select to race channels ready to proceed (often context `Done` channels)
against timers with very low timeouts. Usually, the production code would use
a real timeout, in which case the race is uninteresting, but for testing the timeout
would be set to something very small. And then the test would insist on the
non-timeout case executing, failing if the timeout was reached.
A reduced example might look like:

	select {
	case <-ctx.Done():
		return nil
	case <-time.After(timeout):
		return errors.New("timeout")
	}

Then the test would call this code with `timeout` set to 1ns and fail if the code returned an error.

To fix a test like this, either the caller can be changed to understand that timeouts are possible,
or the code can be changed to prefer the done channel even in the timeout case, like this:

	select {
	case <-ctx.Done():
		return nil
	case <-time.After(timeout):
		// Double-check that Done is not ready,
		// in case of short timeout during test.
		select {
		default:
		case <-ctx.Done():
			return nil
		}
		return errors.New("timeout")
	}

## Debugging

If a program or test fails using Go 1.23 but worked using Go 1.22,
the `asynctimerchan` [GODEBUG setting](/doc/godebug) can be
used to check whether the new timer implementation triggers
the failure:

	GODEBUG=asynctimerchan=0 mytest  # force Go 1.23 timers
	GODEBUG=asynctimerchan=1 mytest  # force Go 1.22 timers

If the program or test consistently passes using Go 1.22 but consistently
fails using Go 1.23, that is a strong sign that the problem is related to timers.

In all the test failures we have observed, the problem has been in the test
itself, not the timer implementation, so the next step is to identify exactly
which code in `mytest` depends on the old implementation.
To do that, you can use [the `bisect` tool](https://pkg.go.dev/golang.org/x/tools/cmd/bisect):

	go install golang.org/x/tools/cmd/bisect@latest
	bisect -godebug asynctimerchan=1 mytest

Invoked this way, `bisect` runs mytest repeatedly, toggling the new timer
implementation on and off depending on the stack trace leading to the
timer call. Using binary search, it narrows down an induced failure to
enabling the new timers during specific stack traces, which it reports.
While `bisect` runs, it prints status messages about its trials,
mainly so that when the test is slow you know it is still running.

An example `bisect` run looks like:

	$ bisect -godebug asynctimerchan=1 ./view.test
	bisect: checking target with all changes disabled
	bisect: run: GODEBUG=asynctimerchan=1#n ./view.test... FAIL (7 matches)
	bisect: run: GODEBUG=asynctimerchan=1#n ./view.test... FAIL (7 matches)
	bisect: checking target with all changes enabled
	bisect: run: GODEBUG=asynctimerchan=1#y ./view.test... ok (7 matches)
	bisect: run: GODEBUG=asynctimerchan=1#y ./view.test... ok (7 matches)
	bisect: target fails with no changes, succeeds with all changes
	bisect: searching for minimal set of disabled changes causing failure
	bisect: run: GODEBUG=asynctimerchan=1#!+0 ./view.test... FAIL (3 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+0 ./view.test... FAIL (3 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+00 ./view.test... ok (1 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+00 ./view.test... ok (1 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+10 ./view.test... FAIL (2 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+10 ./view.test... FAIL (2 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+0010 ./view.test... ok (1 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+0010 ./view.test... ok (1 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+1010 ./view.test... FAIL (1 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!+1010 ./view.test... FAIL (1 matches)
	bisect: confirming failing change set
	bisect: run: GODEBUG=asynctimerchan=1#v!+x65a ./view.test... FAIL (1 matches)
	bisect: run: GODEBUG=asynctimerchan=1#v!+x65a ./view.test... FAIL (1 matches)
	bisect: FOUND failing change set
	--- change set #1 (disabling changes causes failure)
	internal/godebug.(*Setting).Value()
		go/src/internal/godebug/godebug.go:165
	time.syncTimer()
		go/src/time/sleep.go:25
	time.NewTimer()
		go/src/time/sleep.go:144
	time.After()
		go/src/time/sleep.go:202
	region_dash/regionlist.(*Cache).Top()
		region_dash/regionlist/regionlist.go:89
	region_dash/view.(*Page).ServeHTTP()
		region_dash/view/view.go:45
	region_dash/view.TestServeHTTPStatus.(*Router).Handler.func2()
		httprouter/httprouter/params_go17.go:27
	httprouter/httprouter.(*Router).ServeHTTP()
		httprouter/httprouter/router.go:339
	region_dash/view.TestServeHTTPStatus.func1()
		region_dash/view/view.test.go:105
	testing.tRunner()
		go/src/testing/testing.go:1689
	runtime.goexit()
		go/src/runtime/asm_amd64.s:1695

	---
	bisect: checking for more failures
	bisect: run: GODEBUG=asynctimerchan=1#!-x65a ./view.test... ok (6 matches)
	bisect: run: GODEBUG=asynctimerchan=1#!-x65a ./view.test... ok (6 matches)
	bisect: target succeeds with all remaining changes disabled

In this case, the stack trace makes clear exactly which call to `time.After` causes a failure
when using the new timers.

