# Introduction

[Performance Dashboard](http://build.golang.org/perf) does continuous monitoring of performance characteristics of the Go implementation. It notifies codereview threads about any significant changes caused by the commit, allows to see performance changes caused by [recent commits](http://build.golang.org/perf), allows to investigate changes [in detail](http://build.golang.org/perfdetail?commit=fb3d6c1631c3f3141f33a01afb4c0a23ef0ea2cf&commit0=82f48826c6c79a3d5697d5e06cac8451f3dc3c7f&kind=builder&builder=linux-amd64-perf&benchmark=http) .

# Builders

The dashboard uses two builders: linux-amd64 running Ubuntu 14.04 and windows-amd64 running Windows 8.1. Both builders has the same hardware: 2 x Intel Xeon E5620 @ 2.4GHz, 8 HT cores, 12GB RAM.

# Benchmarks

The builders run benchmarks from the [x/benchmarks](https://golang.org/x/benchmarks) repo:
  * ` json `: marshals and unmarshals large json object, in several goroutines independently.
  * ` http `: http client and server serving "hello world", uses persistent connections and read/write timeouts.
  * ` garbage `: parses net package using go/parser, in a loop in several goroutines; half of packages are instantly discarded, the other half is preserved indefinitely; this creates significant pressure on the garbage collector.
  * ` build `: does 'go build -a std'.

# Metrics

Metrics collected are:
  * ` allocated `: amount of memory allocated, per iteration, in bytes
  * ` allocs `: number of memory allocations, per iteration
  * ` cputime `: total CPU time (user+sys from time Unix utility output), can be larger than time when GOMAXPROCS>1, per iteration, in ns
  * ` gc-pause-one `: duration of a single garbage collector pause, in ns
  * ` gc-pause-total `: total duration of garbage collector pauses, per iteration, ns
  * ` latency-50/95/99 `: request latency percentile, in ns
  * ` rss `: max memory consumption as reported by OS, in bytes
  * ` sys-gc `: memory consumed by garbage collector metadata (` MemStats.GCSys `), in bytes
  * ` sys-heap `: memory consumed by heap (` MemStats.HeapSys `), in bytes
  * ` sys-other `: unclassified memory consumption (` MemStats.OtherSys `), in bytes
  * ` sys-stack `: memory consumed by stacks (` MemStats.StackSys `), in bytes
  * ` sys-total `: total memory allocated from OS (` MemStats.Sys `), in bytes
  * ` time `: real time (essentially the same as std Go benchmarks output), per iteration, in ns
  * ` virtual-mem `: virtual memory consumption as reported by OS, in bytes

And for build benchmark:
  * ` binary-size `: size of the go command, in bytes
  * ` build-cputime `: CPU time spent on the build, in ns
  * ` build-rss `: max memory consumption of the build process as reported by OS, in bytes
  * ` build-time `: real time of the build, in ns

# Profiles

The dashboard also collects a set of profiles for every commit, they are available from the [details page](http://build.golang.org/perfdetail?commit=fb3d6c1631c3f3141f33a01afb4c0a23ef0ea2cf&commit0=82f48826c6c79a3d5697d5e06cac8451f3dc3c7f&kind=builder&builder=linux-amd64-perf&benchmark=http). For usual benchmarks [CPU](http://build.golang.org/log/b023711522ca6511f2c9bfb46cdfb511fd77e967) and [memory](http://build.golang.org/log/06bd072aa0dec4936a05b7aa13b9f906b6989865) profiles are collected. For build benchmark - [perf profile](http://build.golang.org/log/34c4f0c7b7ea3521e5356b91775a026607e72d44), [per-process split of CPU time](http://build.golang.org/log/da517b4f6892af8a6b4900dbe58311b665ced00f) and [per-section size](http://build.golang.org/log/fc4287d6a9e280bf35c572c038dbc4414d60bcf8).

# Perf Changes View

The [view](http://build.golang.org/perf) allows to see aggregate information about significant performance changes caused by recent commits.

Rows:
  * The first row shows difference between the latest release and tip.
  * The rest of the rows show deltas caused by individual commits.

Columns:
  * The first column is commit hash.
  * Second - number of benchmarks that were executed for the commit to far.
  * Third - metric name, or the special 'failure' metric for build/runtime crashes.
  * Fourth - negative deltas.
  * Fifth - positive deltas.
  * The rest describe commit.

You can click on any positive/negative delta to see details about the change.
