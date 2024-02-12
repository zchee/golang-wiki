---
title: PerformanceMonitoring
---

The Go project monitors the performance characteristics of the Go implementation
as well as that of subrepositories like golang.org/x/tools.

## Benchmarks

`golang.org/x/benchmarks/cmd/bench` is the entrypoint for our performance tests.
For Go implementations, this runs both the
[Sweet](https://golang.org/x/benchmarks/sweet) (end-to-end benchmarks)
and [bent](https://golang.org/x/benchmarks/cmd/bent) (microbenchmarks)
benchmarking suites.

For the `golang.org/x/tools` project, it runs the repository's benchmarks.

These benchmarks can all be invoked manually, as can `cmd/bench`, but using both
Sweet and bent directly will likely offer a better user experience.
See their documentation for more details.

## Performance testing principles

### Change with the times

Our set of benchmarks is curated.
It is allowed to change over time.
Sticking to a single benchmark set over a long period of time can easily land
us in a situation where we're optimizing for the wrong thing.

### Always perform a comparison

We never report performance numbers in isolation, and only relative to some
baseline.
This strategy comes from the fact that comparing performance data taken far
apart in time, even on the same hardware, can result in a lot of noise that
goes unaccounted for.
The state of a machine or VM on one day is likely to be very different than
the state of a machine or VM on the next day.

We refer to the tested version of source code as the "experiment" and the
baseline version of source code as the "baseline."

## Presubmit

Do you have a Gerrit change that you want to run against our benchmarks?

Select a builder containing the word `perf` in the "Choose Tryjobs" dialog that
appears when selecting a [SlowBot](https://go.dev/wiki/SlowBots).

There are two kinds of presubmit builders for performance testing:
- `perf_vs_parent`, which measures the performance delta of a change in isolation.
- `perf_vs_tip`, which measures the performance delta versus the current
  tip-of-tree for whichever repository the change is for.
  (Remember to rebase your change(s) before using this one!)

There's a third special presubmit builder for the tools repository as well which
contains the string `perf_vs_gopls_0_11`.
This measures the performance delta versus the `release-branch-gopls.0.11` branch
of the tools repository.

## Postsubmit

The [performance dashboard](http://perf.golang.org/dashboard) provides
continuous monitoring of benchmark performance for every commit that is made to
the main Go repository and other subrepositories.
The dashboard, more specifically, displays graphs showing the change in certain
performance metrics (also called "units") over time for different benchmarks.
Use the navigation interface at the top of the page to explore further.

The [regressions page](https://perf.golang.org/dashboard/?benchmark=regressions)
displays all benchmarks in order of biggest regression to biggest improvement,
followed by all benchmarks for which there is no statistically clear answer.

On the graphs, red means regression, blue means improvement.

### Baselines

In post-submit, the baseline version for Go repository performance tests is
automatically determined.
For performance tests against changes on release branches, the baseline is always
the latest release for that branch (for example, the latest minor release for
Go 1.21 on `release-branch.go1.21`).
For performance tests against tip-of-tree, the baseline is always the latest
overall release of Go.
This is indicated by the name of the builder that produces these benchmark
esults, which contains the string `perf_vs_release`.
What this means is that on every minor release of Go, the baseline shifts.
These baseline shifts can be observed in the [per-metric view](#per-metric-view).

Performance tests on subrepositories typically operate against some known
long-term fixed baseline.
For the tools repository, it's the tip of the `release-branch-gopls.0.11`
branch.

### Per-metric view

Click on any graph's performance metric name to view a more detailed timeline
of the performance deltas for that metric.

![Image displaying which link to click to reach the per-metric
page.](images/performance-monitoring-per-metric-link.png)

This view is particularly useful for identifying the culprit behind a regression
and for pinpointing the source of an improvement.

Sometimes, a performance change happens because a benchmark has changed or
because the baseline version being used as changed.
This view also displays information about the baseline versions and the version
of `golang.org/x/benchmarks` that was used to produce the results to help identify
when this happens.
