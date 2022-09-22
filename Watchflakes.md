Watchflakes is a program that triages apparent test flakes on the build.golang.org dashboards.

An apparent test flake is a failure that:

 - is not on a completely failing builder.
 - is not on an [excluded builder](https://go.dev/issue/55166).
 - is not running a commit that failed on 4 or more builders.
 - is not part of a run of 4 or more failing commits on its builder.

Watchflakes posts every apparent test flake to an issue in the [Test Flakes project](https://github.com/orgs/golang/projects/20).

Every issue description in the Test Flakes project starts with a pattern for the failures relevant to that issue:
For example, the markdown for #55260's description starts with:

	```
	#!watchflakes
	post <- pkg == "cmd/go" && test == "" && `unexpected files left in tmpdir`
	```

Watchflakes matches every apparent test flake against the patterns in the issues:

 - If a flake matches a pattern in an issue, it is posted to that issue.
 - If a flake matches a pattern in multiple issues, it is posted to the lowest-numbered issue.
 - If a flake does not match a pattern in any issue, watchflakes creates a new issue with a pattern matching the package and test case that failed.

The newly created issue's pattern is often too broad and should be edited to make it more specific to the actual failure.
Sending a failure to the lowest-numbered matching issue ensures that creating a broad default pattern
for a new failure does not “steal” failures from earlier issues,
nor does it spam the new issue with unrelated failures in the same test that are already separately tracked.

Watchflakes places newly created issues in the Test Flakes project and adds the NeedsInvestigation label.
These issues start out with no status (not Active, not Done).
Issues with no status need to be inspected by a person,
who should usually refine the pattern to capture the salient information about the failure.
Issues that have been checked can then be moved to Active.
GitHub automatically moves issues from Active to Done when they are closed.

Watchflakes considers issues of any status when matching a new failure.
If it finds a new failure for a closed issue, it will post the failure and reopen the issue.
So it is okay to close an issue when a fix lands, instead of having to wait a few weeks
to see if the failure is really gone: if a new failure arrives, the issue will be reopened automatically.

Watchflakes maintains no state of its own: all the state is in the GitHub issues.
Every time it runs, it considers the past 60 days of build dashboard failures
and makes sure that every apparent flake is accounted for in the Test Flakes project.
If a failure matching an issue has already been posted to that issue, watchflakes doesn't post it again, of course.
And if an issue is edited to update its pattern to exclude certain failures,
watchflakes doesn't remove its old posts, but it does look for a different matching issue for those failures,
including possibly creating a new one.

## Syntax

The watchflakes stanza in each issue must appear at the top of the issue description.
It must be a code block (either fenced with ```` ``` ```` or indented), and the first line must be `#!watchflakes`,
to keep watchflakes from misinterpreted unrelated code blocks.

The rest of the block is a small watchflakes script. Comments to the end of the line are introduced with `#`.
The script is a sequence of rules, each of which has the form `action <- pattern`
(send matches for pattern to the action).

### Actions

The actions are:

 - `post` posts the failure to the issue in which the script appears.
 - `skip` ignores the failure, throwing it on the floor. This action should be used only rarely (for example, to set policy like in #55166).
 - `default` is a lower-priority version of post. If an issue has a `post` or `skip` matching the failure, watchflakes does that instead.
    But if there are no other matches, watchflakes considers the `default` pattern matches.
    (And then if there aren't any `default` matches, watchflakes creates a new issue.)

### Records

The input to the pattern is a record with named fields, each of which has a string value:

 - `pkg` is the full import path of the package that failed to build or that failed its test.

 - `test` is the name of the test function in the package that failed.

 - `mode` is `build` or `test` depending on whether this is a build failure or a test failure.

 - `output` is the output from the failing test. This output stops just before the final `FAIL` line printed when the test binary exits.
   It does not include output from other test cases that also failed in the same run,
   nor any context that was printed by all.bash or the buildlet before the test started.

 - `log` is the entire failed build log.

 - `snippet` is the shortened form of `output` that will be posted to the issue itself.
   Matches should almost always use `output` instead.

 - `builder` is the name of the builder that ran the test (like `dragonfly-amd64-622`).

 - `repo` is the name of the repo being tested (`go`, `net`, `tools`, ...).

 - `goos` is the GOOS value (`linux`, `windows`, ...).

 - `goarch` is the GOARCH value (`amd64`, `mips64le`, ...).

 - `date` is the date of the commit being tested, in the form `2006-01-02T15:04:05`.
   There is no date comparison logic; use string comparisons instead.
   Comparing dates should be used rarely.

 - `section` is the section of the build log in which the failure occurred.
   In all.bash output, the section is introduced by `#####`,
   and each of the `Building` lines during bootstrap is considered its own section as well.
   In subrepos, the `:: Running` lines each introduce a section named for the go command being run
   (for example `go test golang.org/x/tools/...`).

   Most patterns don't need to use `section`. It is most helpful for tests in the main repo
   that rerun tests with an alternate execution environment.

### Patterns

The pattern is a boolean expression in a Go-like syntax allowing
||, &&, !, (, and ) for building complex expressions;
==, !=, <, <=, >, and >= for comparing fields against against string literals;
and ~ and !~ for matching against regular expressions.

All string comparisons must have a field name on the left and a double-quoted string literal on the right, as in
`builder == "linux-amd64-alpine"` or `goos == "

All regular expression matches must have a field name on the left and a back-quoted string literal on the right, as in
`` builder ~ `corellium` ``.

A back-quoted string literal by itself is taken to be a comparison against the `output` field,
which is appropriate for the vast majority of regular expressions in patterns.

## Examples

Putting this all together, here are some example scripts.

	#!watchflakes
	post <- pkg == "net/http" && test == "TestHandlerAbortRacesBodyRead"

This script in #55277 was created automatically by watchflakes in response
to a build run that failed in http.TestHandlerAbortRacesBodyRead.
The specific failure that prompted the issue createion was a timeout.
If more failures with different root causs were found in that test, it might become
appropriate to add `` && `panic: test timed out` `` or otherwise refine the pattern.

	#!watchflakes
	post <- goos == "openbsd" && `unlinkat .*: operation not permitted`

This script in #49751 collects failures on openbsd caused by unexpected EPERM
errors from os.Remove calling unlinkat. These failures cause problems in a variety of tests,
so there is no condition on `pkg` or `test`.

	#!watchflakes
	post <- pkg ~ `^cmd/go` && `appspot.com.*: 503`

This script in #54608 tracks network problems with 503 responses from appspot.com
in any tests in the cmd/go/... package hierarchy, not just cmd/go itself.

	#!watchflakes
	post <- goos == "windows" &&
	        (`dnsquery: DNS server failure` || `getaddrinfow: This is usually a temporary error`)

This script in #55165 matches specific DNS failures in any test on builders running Windows.

	#!watchflakes
	post <- builder == "darwin-arm64-12" && pkg == "" && test == ""

This script in #55312 was created automatically by watchflakes to track failures on
the darwin-arm64-12 builder that happen before a specific package test can run.

	#!watchflakes
	# note: sometimes the URL is printed with one /
	default <- `(Get|read) "https://?(goproxy.io|proxy.golang.com.cn|goproxy.cn)`

This script in #55163 matches errors using certain non-standard Go proxies.
It uses `default` to allow other issues to take ownership of more specific failures caused by these proxies.
Failures not matching other issues go to #55163 instead of creating new issues.

	#!watchflakes
	default <- `: internal compiler error:`

This script in #55257 matches compiler failures in any build, no matter what package or repo is being tested.
It uses `default` for the same reasons as the previous example: so that issues matching specific
compiler errors can still be filed, but failures not matching other issues are grouped into #55257
instead of creating new issues assigned to the specific test that happened to trigger the problem.
