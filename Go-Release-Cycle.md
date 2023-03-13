This wiki page is maintained by the Go team. Please
[send comments to golang-dev](https://groups.google.com/group/golang-dev) or
[file issues](https://go.dev/issue) instead of making changes directly.

Short link: https://go.dev/s/release.

## Overview

Go is released every six months. Each release cycle is broken down into a
development phase lasting about 4 months, followed by a 3-month period of
testing and polishing called the release freeze. If everything goes well, work
on the next release begins before the previous release has shipped, resulting in
an overlap of about a month.

After the initial release of a version, it is supported with minor releases that
fix severe bugs and security issues.

## Timeline

The current release cycle is aligned to start in mid-January and mid-July of
each year. The target milestones for a release cycle are as described below. We
try to hit the targets as closely as possible, while still delivering a quality
release.

To give the team time to prepare, and to address unexpected problems, we prefer
to do release work early or mid-week. That means that exact dates will vary year
to year, so milestones are specified as weeks in a particular month. Week 1 is
the week starting on the first Monday of the month. All dates are subject to
change based on the year's holiday timings.

![release](https://user-images.githubusercontent.com/24611692/223832580-b613c098-cd8b-4d48-b5c4-cf349e7cc269.svg)

#### January / July week 1: Planning for release begins.

Planning of major work for upcoming release cycle is announced on
[golang-dev](https://groups.google.com/group/golang-dev).

Example: [Go 1.20](https://groups.google.com/g/golang-dev/c/V8ez4YunkeE)

#### January / July week 3: Release work begins.

Once the prior release has entered its final stabilization period, the tree
opens for general development. All kinds of development are welcome during this
period. It's preferable for large or particularly risky changes to land well before
the end of the development window, so that there's time to fix any
problems that arise with them.

#### May / November week 4: Release freeze begins.

This milestone begins the second part of the release cycle, the release freeze.
The release freeze applies to the entire main repository as well as to the code
in subrepositories that is needed to build the binaries included in the release,
particularly vet and all its dependencies in the tools subrepository.

During the freeze, only bug fixes and doc updates are accepted. On occasion new
work may be done during the freeze, but only in exceptional circumstances and
typically only if the work was proposed and approved before the cutoff. Such
changes must be low risk. See [freeze exceptions](#freeze-exceptions) below.

This part of the release cycle is focused on improving the quality of the
release, by testing it and fixing bugs that are found. However, every fix must
be evaluated to balance the benefit of a possible fix against the cost of now
having not as well tested code (the fix) in the release. Early in the release
cycle, the balance tends toward accepting a fix. Late in the release cycle, the
balance tends toward rejecting a fix, unless a case can be made that the fix is
both low risk and high reward.

Examples of low risk changes appropriate late in the cycle include changes to
documentation and fixes to new features being introduced in the current release
(since there is no chance of introducing a regression compared to an earlier
release).

Shortly after the freeze begins, nearly all known bugs should have been fixed or
explicitly postponed (either to the next release or indefinitely). The remainder
should usually be tracked as release blockers and worked on urgently.

#### June / December week 2: Release candidate 1 issued.

A release candidate is meant to be as close as possible to the actual release
bits. Issuing a release candidate is an indication that the Go team has high
confidence that the tree is free of critical bugs. In particular, because Google
continuously tracks the development version of Go, by the time a release
candidate is issued, a close approximation of it will have been running in
production at Google for at least a week or two.

Once a release candidate is issued, only documentation changes and changes to
address critical bugs should be made. In general the bar for bug fixes at this
point is even slightly higher than the bar for bug fixes in a minor release. We
may prefer to issue a release with a known but very rare crash than to issue a
release with a new but not production-tested fix.

If critical bugs are reported and fixed, additional release candidates may be
issued, but typically not more than one every two weeks.

Again, a release candidate is meant to be bug-free, as much as possible.
Organizations are encouraged to deploy it in production settings after
appropriate organization-specific testing.

The calm period between a release candidate and the final release is a good time
for additional testing or for discussing the next release (see the planning
milestone above).

#### August / February week 2: Release issued.

Finally, the release itself!

A release should not contain significant changes since the last release
candidate: it is important that all code in the release has been well tested.
Issuing a release is an indication that release testing has confirmed the
release candidate's high confidence that the tree is free of critical bugs.

Even if a release goes smoothly and there's spare time, we prefer to stay on
schedule. Extra testing can only improve the stability of a release, and it also
gives developers working on the Go release more time to think about and plan the
next release before code changes start pouring in again.

By the time of the final release, Google will have been using this version of Go
for nearly two months. While Google's successful use does not guarantee the
absence of problems, our experience has been that it certainly helps improve the
quality of the release. We strongly encourage other organizations to test
release candidates as aggressively as they are able and to report problems that
they find.

Once a release is stabilized, work on the next release, including code reviews
and submission of new code, can begin, and the cycle repeats. Note that if a
release is delayed, work on the next release may be delayed as well.

## Release Maintenance

A minor release is issued to address one or more critical problems for which
there is no workaround (typically related to stability or security). The only
code changes included in the release are the fixes for the specific critical
problems. Important documentation-only changes and safe test updates (such as
disabling tests), may also be included as well, but nothing more. Minor releases
preserve backwards compatibility as much as possible, and don't introduce new
APIs.

Minor releases to address problems (including security issues) for Go 1.x stop
once Go 1.x+2 is released. For more about security updates, see the
[security policy](https://go.dev/security).

See also the [MinorReleases](https://go.dev/wiki/MinorReleases) wiki page.

## Freeze Exceptions

Any exceptions to the freeze must be communicated to and explicitly approved by
the Go Release Team before the freeze. If you’d like to request an exception,
please file an issue in the issue tracker with "[freeze exception]" as a suffix
and include "CC @golang/release" ([example](https://go.dev/issue/42747)). We
will address any requests on a case-by-case basis with a strong preference for
not permitting changes after the freeze.

## Historical note

A version of this schedule, with a shorter development window, was originally
adopted for the Go 1.7 release in 2016. After years of difficult releases,
testing and process improvements in 2022 and 2023 led to a timely 1.19 release.
For 1.20, the development window was expanded with a late freeze and early thaw.
These changes were formalized for the 1.21 release. We anticipate continuing to
ship on time.