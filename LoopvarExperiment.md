---
title: LoopvarExperiment
---

For Go 1.22, the Go team is considering changing the semantics of for loop variables to prevent unintended sharing in per-iteration closures and goroutines. Go 1.21 contains a preliminary implementation of the change, enabled by setting `GOEXPERIMENT=loopvar` when building your program. We invite anyone who wants to help us understand the effects of the change to try using `GOEXPERIMENT=loopvar` and let us know about any problems or successes encountered.

This page answers frequently asked questions about the change.

## How do I try the change?

Using Go 1.21, build your program using `GOEXPERIMENT=loopvar`, as in 

	GOEXPERIMENT=loopvar go install my/program
	GOEXPERIMENT=loopvar go build my/program
	GOEXPERIMENT=loopvar go test my/program
	GOEXPERIMENT=loopvar go test my/program -bench=.
	...

## What is the problem this solves?

Consider a loop like:

```go
	func TestAllEvenBuggy(t *testing.T) {
		testCases := []int{1, 2, 4, 6}
		for _, v := range testCases {
			t.Run("sub", func(t *testing.T) {
				t.Parallel()
				if v&1 != 0 {
					t.Fatal("odd v", v)
				}
			})
		}
	}
```

This test aims to check that all the test cases are even (they are not!), but it passes without `GOEXPERIMENT=loopvar`. The problem is that t.Parallel stops the closure and lets the loop continue, and then it runs all the closures in parallel when `TestAllEvenBuggy` returns. By the time the if statement in the closure executes, the loop is done, and v has its final iteration value, 6. All four subtests now continue executing in parallel, and they all check that 6 is even, instead of checking each of the test cases.

Another variant of this problem is

```go
	func TestAllEven(t *testing.T) {
		testCases := []int{0, 2, 4, 6}
		for _, v := range testCases {
			t.Run("sub", func(t *testing.T) {
				t.Parallel()
				if v&1 != 0 {
					t.Fatal("odd v", v)
				}
			})
		}
	}
```

This test is not incorrectly passing, since 0, 2, 4, and 6 are all even, but it is also not testing whether it handles 0, 2, and 4 correctly. Like `TestAllEvenBuggy`, it tests 6 four times.

Another less common but still frequent form of this bug is capturing the loop variable in a 3-clause for loop:

```go
	func Print123() {
		var prints []func()
		for i := 1; i <= 3; i++ {
			prints = append(prints, func() { fmt.Println(i) })
		}
		for _, print := range prints {
			print()
		}
	}
```

This program looks like it will print 1, 2, 3, but in fact prints 4, 4, 4.

This kind of unintended sharing bug hits all Go programmers, whether they are just starting to learn Go or have been using it for a decade. Discussion of this problem is one of the [earliest entries in the Go FAQ](https://go.dev/doc/faq#closures_and_goroutines).

Here is a [public example of a production problem caused by this kind of bug](https://bugzilla.mozilla.org/show_bug.cgi?id=1619047), from Let's Encrypt. The code in question said:

```go
// authz2ModelMapToPB converts a mapping of domain name to authz2Models into a
// protobuf authorizations map
func authz2ModelMapToPB(m map[string]authz2Model) (*sapb.Authorizations, error) {
	resp := &sapb.Authorizations{}
	for k, v := range m {
		// Make a copy of k because it will be reassigned with each loop.
		kCopy := k
		authzPB, err := modelToAuthzPB(&v)
		if err != nil {
			return nil, err
		}
		resp.Authz = append(resp.Authz, &sapb.Authorizations_MapElement{Domain: &kCopy, Authz: authzPB})
	}
	return resp, nil
}
```

Note the `kCopy := k` guarding against the `&kCopy` used at the end of the loop body. Unfortunately, it turns out that `modelToAuthzPB` kept a pointer to a couple fields in `v`, which is impossible to know when reading this loop.

The initial impact of this bug was that Let's Encrypt needed to [revoke over 3 million improperly-issued certificates](https://community.letsencrypt.org/t/revoking-certain-certificates-on-march-4/114864). They ended up not doing that because of the negative impact it would have had on internet security, instead [arguing for an exception](https://bugzilla.mozilla.org/show_bug.cgi?id=1619179), but that gives you a sense of the kind of impact. 

The code in question was carefully reviewed when written, and the author was clearly aware of the potential problem, since they wrote `kCopy := k`, and yet it _still had a major bug_, one that is not visible unless you also know exactly what `modelToAuthzPB` does.

## What is the proposed solution?

The solution is to make loop variables declared in for loops using `:=` be a different instance of the variable on each iteration. This way, if the value is captured in a closure or goroutine or otherwise outlasts the iteration, later references to it will see the value it had during that iteration, not a value overwritten by a later iteration.

For range loops, the effect is as if each loop body starts with `k := k` and `v := v` for each range variable.
In the Let's Encrypt example above, the `kCopy := k` would not be necessary, and the bug caused by not having `v := v` 
would have been avoided.

For 3-clause for loops, the effect is as if each loop body starts with `i := i` and then the reverse assignment
happens at the end of the loop body, copying the per-iteration `i` back out to the `i` that will be used to
prepare for the next iteration. This sounds complex, but in practice all common for loop idioms continue
to work exactly as they always have. The only time the loop behavior changes is when `i` is captured and shared
with something else. For example, this code runs as it always has:

```go
	for i := 0;; i++ {
		if i >= len(s) || s[i] == '"' {
			return s[:i]
		}
		if s[i] == '\\' { // skip escaped char, potentially a quote
			i++
		}
	}
```

For full details, see [the design document](https://go.googlesource.com/proposal/+/master/design/60078-loopvar.md).

## Can this change break programs?

Yes, it is possible to write programs that this change would break. For example, here is a surprising way to add the values in a list using a single-element map:

```go
func sum(list []int) int {
	m := make(map[*int]int)
	for _, x := range list {
		m[&x] += x
	}
	for _, sum := range m {
		return sum
	}
	return 0
}
```

It depends on the fact that there is only one `x` in the loop, so that `&x` is the same in each iteration. With `GOEXPERIMENT=loopvar`, `x` escapes the iteration, so `&x` is different on each iteration, and the map now has multiple entries instead of a single entry.

And here is a surprising way to print the values 0 through 9:

```go
	var f func()
	for i := 0; i < 10; i++ {
		if i == 0 {
			f = func() { print(i) }
		}
		f()
	}
```

It depends on the fact that the `f` initialized on the first iteration “sees” the new value of `i` each time it is called. With `GOEXPERIMENT=loopvar`, it prints 0 ten times.

Although it is possible to construct artificial programs that break using `GOEXPERIMENT=loopvar`, we have yet to see any real programs
that execute incorrectly.

C# made a similar change in C# 5.0 and [they also reported](https://github.com/golang/go/discussions/56010#discussioncomment-3788526) having very few problems caused by the change.

More breaking or surprising cases are shown in [here](https://github.com/golang/go/issues/60078#issuecomment-1544324607) and [here](https://github.com/golang/go/issues/60078#issuecomment-1546019456).

## How often does the change break real programs?

Empirically, almost never. Testing on Google's codebase found many tests were fixed. It also identified some buggy tests incorrectly passing due to bad interactions between loop variables and `t.Parallel`, like in `TestAllEvenBuggy` above. We rewrote those tests to correct them.

Our experience suggests that the new semantics fixes buggy code far more often than it breaks correct code. The new semantics only caused test failures in about 1 of every 8,000 test packages (all of them incorrectly passing tests), but running the updated Go 1.20 `loopclosure` vet check over our entire code base flagged tests at a much higher rate: 1 in 400 (20 in 8,000). The `loopclosure` checker has no false positives: all the reports are buggy uses of `t.Parallel` in our source tree. That is, about 5% of the flagged tests were like `TestAllEvenBuggy`; the other 95% were like `TestAllEven`: not (yet) testing what it intended, but a correct test of correct code even with the loop variable bug fixed.

Google has been running with the new loop semantics applied to all for loops in the standard production toolchain since early May 2023 with not a single reported problem (and many cheers).

For more details about our experience at Google, see [this writeup](https://go.googlesource.com/proposal/+/master/design/60078-loopvar.md#fixes).

We also [tried the new loop semantics in Kubernetes](https://github.com/golang/go/issues/60078#issuecomment-1556058025). It identified two newly failing tests due to latent loop variable scoping-related bugs in the underlying code. For comparison, updating Kubernetes from Go 1.20 to Go 1.21 identified three newly failing tests due to reliance on undocumented behaviors in Go itself. The two tests failing due to loop variable changes are not a significant new burden compared to an ordinary release update.

## Will the change make programs slower by causing more allocations?

The vast majority of loops are unaffected. A loop only compiles differently if the loop variable has its address taken (`&i`) or is captured by a closure. 

Even for affected loops, the compiler's escape analysis may determine that the loop variable can still be stack-allocated, meaning no new allocations. 

However, in some cases, an extra allocation will be added. Sometimes, the extra allocation is inherent to fixing a latent bug. For example, Print123 is now allocating three separate ints (inside the closures, it turns out) instead of one, which is necessary to print the three different values after the loop finishes. In rare other cases, the loop may be correct with a shared variable and still correct with separate variables but is now allocating N different variables instead of one. In very hot loops, this might cause slowdowns. Such problems should be obvious in memory allocation profiles (using `pprof --alloc_objects`).

Benchmarking of the public “bent” bench suite showed no statistically significant performance difference over all, and we've observed no performance problems in Google's internal production use either. We expect most programs to be unaffected.

## If the proposal is accepted, how will the change be deployed?

Consistent with Go's general [approach to compatibility](https://tip.golang.org/doc/godebug), the new for loop semantics will only apply when the package being compiled is from a module that contains a `go` line declaring Go 1.22 or later, like `go 1.22` or `go 1.23`. This conservative approach ensures that _no programs will change behavior due to simply adopting the new Go toolchain_. Instead, each module author controls when their module changes to the new semantics.

The `GOEXPERIMENT=loopvar` trial mechanism does not use the declared Go language version: it applies the new semantics to every for loop in the program unconditionally. This gives a worst case behavior to help identify the maximum possible impact of the change.

## Can I see a list of places in my code affected by the change?

Yes. You can build with `-gcflags=all=-d=loopvar=2` on the command line. That will print a warning-style output line for every loop that is compiling differently, like:

	$ go build -gcflags=all=-d=loopvar=2 cmd/go
	...
	modload/import.go:676:7: loop variable d now per-iteration, stack-allocated
	modload/query.go:742:10: loop variable r now per-iteration, heap-allocated

The `all=` prints about changes to all packages in your build. If you omit the `all=`, as in `-gcflags=-d=loopvar=2`, only the
packages you name on the command line (or the package in the current directory) will emit the diagnostic.

## My test fails with the change. How can I debug it?

A new tool called `bisect` enables the change on different subsets of a program to identify which specific loops trigger a test failure when compiled with the change. If you have a failing test, `bisect` will identify the specific loop that is causing the problem. Use:

	go install golang.org/x/tools/cmd/bisect@latest
	bisect -compile=loopvar go test

See the [bisect transcript section of this comment](https://github.com/golang/go/issues/60078#issuecomment-1556058025) for a real-world example, and [the bisect documentation](https://pkg.go.dev/golang.org/x/tools/cmd/bisect) for more details.

## Does this mean I don’t have to write x := x in my loops anymore?

Not yet. But we hope that in a future version of Go you won't have to, perhaps even Go 1.22.

## How can I send feedback?

The [proposal issue](https://github.com/golang/go/issues/60078) is the place to discuss the proposal. However, please note that arguments about what is intuitive or natural are not productive: different people can quite reasonably have different opinions of what is intuitive or natural.

Instead, the most important feedback you can contribute to the discussion is _empirical data about using the change on real codebases_:

 - What fraction of tests started failing with `GOEXPERIMENT=loopvar`?
 - Were any of the newly failing tests caused by `GOEXPERIMENT=loopvar` breaking correct production code, as opposed to identifying buggy code or tests?
 - Do any of your important, real-world benchmarks get significantly slower or use significantly more memory?


 

