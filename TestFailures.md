# TestFailures

If you notice a failure in a test in the Go project, what should you do?

## Goals of testing

The goal of writing (and running) tests for a Go package is to learn about the
behavior of that package and its dependencies.

A test failure for a Go package may give us information about:
* implementation defects in the package or its dependencies,
* mistaken assumptions about the package API,
* bugs in the test itself (such as invalid assumptions about timing),
* unexpectedly high resource requirements (such as RAM or CPU time), or
* bugs in the underlying platform or defects in the test infrastructure (which
  may need to be escalated or worked around).

In some cases, the cause of a test failure might not be clear: it might be
caused by _more than one_ of the above conditions. Much like repeating a
scientific experiment, allowing a test to fail multiple times can sometimes
provide more information from the specific pattern of failures.

However, if a test fails without telling us anything new, then the test is not
fulfilling its purpose.

## Finding test failures

A test failure is typically noticed from:
* the [Go build dashboard](https://build.golang.org), especially during [builder
  triage](https://go.dev/issue/52653);
* TryBot or [SlowBot](https://go.dev/wiki/SlowBots) failures on a pending
  change;
* running `go test` on a specific package or packages, either working within a
  Go project repository or as part of (say) `go test all` in a user's own
  module;
* or running `all.bash` or `all.bat` when [installing from
  source](https://go.dev/doc/install/source#install) or [testing a contributed
  change](https://go.dev/doc/contribute#testing).

## Triaging a test failure

Once we have noticed a failure, we need to _triage_ it.
The goal of triage is to identify:

1. Is the information from the failure new?
2. Who is best equipped to analyze the new information from the failure?

### Identifying new information

Start by searching the [open issues](https://go.dev/issue) for key details from
the failure, such as the name of the failing test and/or other distinctive
fragments of the error text (such as error codes).

If you find an existing issue, first check the issue discussion to see whether
the failure has already been fixed, and whether the information from your failure
contributes relevant new information. If so, _comment on it_ with details:
* describe what Go version you were testing (`go version`)
* how and where you were running the test, such as:
   * `go env` output
   * your machine and OS configuration
   * your network configuration and status
* whether or how often you are able to reproduce the failure.

Ideally, attach or link to the full test logs (possibly in a `<details>` block).

If you don't find an existing issue, file a new one.

### Filing an issue

Paste in enough of the test log for future reporters to be able to search for
the issue, including the name of the test and any distinctive parts of its log
output. (If the test log is long — such as if it contains a large goroutine
dump — consider posting a shorter excerpt and/or enclosing the complete failure
message in a `<details>` block.)

You can use the
[`fetchlogs`](https://pkg.go.dev/golang.org/x/build/cmd/fetchlogs) and
[`greplogs`](https://pkg.go.dev/golang.org/x/build/cmd/greplogs) tools to
search for similar failures in the build dashboard:

```
# download recent logs
fetchlogs -n 1024 -repo all
```
```
# search logs for some regexp describing the failure message
greplogs -l -e $FAILURE_REGEXP
```

If the failure appears to be specific to a package, consult
https://dev.golang.org/owners to find the maintainers of that package and mention
them on the issue. (If no owners are listed for the package, check the recent
history of the package at https://cs.opensource.google/go and/or escalate to
someone who can help to identify a relevant owner — and consider updating the
[owners
table](https://cs.opensource.google/go/x/build/+/master:devapp/owners/table.go)
with what you learn!)

If the failure appears to be specific to a `GOOS` or `GOARCH` label the issue
with the corresponding GOOS and/or GOARCH labels, and mention the relevant
subteam(s) of
[@golang/port-maintainers](https://github.com/orgs/golang/teams/port-maintainers)
on the issue.

If the failure appears to affect at least one
[first class port](https://go.dev/wiki/PortingPolicy#first-class-ports),
add the issue to the current release milestone and label it
[`release-blocker`](https://github.com/golang/go/labels/release-blocker).
Otherwise, add the issue to the `Backlog` milestone.

If the failure appears to be specific to a builder (such as a network
connectivity issue, or a platform bug requiring a system update), consult
[`x/build/dashboard/builders.go`](https://cs.opensource.google/go/x/build/+/master:dashboard/builders.go)
to find the maintainer for that builder and mention them on the issue.
(For builders without an explicit maintainer listed, instead mention
the [@golang/release](https://github.com/orgs/golang/teams/release) team.)

## Addressing a test failure

Once an issue has been filed for a test failure, the relevant package, port,
and/or builder maintainers should examine the information gleaned from the test
failure and decide how to _address_ it, by doing one or more of:

* _revert_ a change to the code or the test infrastructure believed to have
  introduced the problem,
* _fix_ (or apply a workaround for) the root cause of the failure,
* _collect_ more information, by subscribing to issue updates and/or running
  more tests,
* _report_ an underlying defect in a dependency, platform, or test
  infrastructure, and/or
* _deprioritize_ the failure, by skipping the failure on affected platforms (or
  marking those platforms as broken) and then moving the issue to a future or
  `Backlog` milestone and/or removing the `release-blocker` label.

When a maintainer decides to deprioritize a test failure, they determine that
_additional failures of the test will not provide useful new information_. At
that point, the test no longer fulfills its purpose, and the maintainer should
suppress the failure — typically by adding a call to
[`testenv.SkipFlaky`](https://pkg.go.dev/internal/testenv#SkipFlaky) or
[`t.Skipf`](https://pkg.go.dev/testing#F.Skipf).

### Skipping a test failure

When we add a call to `testenv.SkipFlaky`, our goal is to eliminate failure
modes that do not provide new information while still preserving as much of the
value of the test as is feasible.

* If the observed failure is only one of several possible failure modes for
  the test, skip the test only for that failure mode.

   * For example, if the error is always something specific like
     `syscall.ECONNRESET`, use `errors.Is` to check for that specific error.

* If the failure is believed to affect all versions of a particular `GOOS`
  and/or `GOARCH`, or the affected versions cannot be identified, check against
  `runtime.GOOS` and/or `runtime.GOARCH` and skip only the affected platform.

* If the failure is due to a bug on a _specific version_ of a platform, skip the
  test based on `testenv.Builder` or the `GO_BUILDER_NAME` environment variable.
  (If the test fails for external Go users, they have the option to upgrade to
  an unaffected version of the platform — and they probably ought to see the
  test failure to find out that the bug exists!)

   * Also consider adding another environment variable that users and contributors
     can set to acknowledge the bug and suppress the failure.

### Marking a builder or port as broken

A platform bug or bug in a core package (such as `os`, `net`, or `runtime`) may
impact so many tests that the failures are not feasible to skip, or may manifest
as a failure at compile or link time. If such a bug occurs, the options are more
limited: if we cannot revert a change or fix or work around the root cause, and
don't need to collect more information, we can only deprioritize the failure by
marking the _entire builder or platform_ as broken.

To mark a builder as broken, edit its configuration in
[`x/build/dashboard/builders.go`](https://cs.opensource.google/go/x/build/+/master:dashboard/builders.go)
to add an issue in the `KnownIssue` field; note that builders with known issues
will generally be skipped during dashboard triage.

A broken builder for a
[first class port](https://go.dev/wiki/PortingPolicy#first-class-ports)
should have its known issue(s) labeled `release-blocker`, pending a decision
to either fix the builder or drop support for the affected version of the
platform.

If all of the builders for a secondary port are broken, the port itself may be
considered broken. [Discussion
#53060](https://github.com/golang/go/discussions/53060)
aims to resolve the question of how broken secondary ports should be handled.