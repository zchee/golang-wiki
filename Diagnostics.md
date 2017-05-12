# Diagnostics


The Go ecosystem provides a large suite of APIs and tools to diagnose logical and performance problems in Go programs. This document summarizes the available tools and helps Go users to pick the right tool for their specific problem.

Diagnostics solutions can be categorized into the following groups:

* **Profiling**: Profiling tools analyze the complexity and costs of a Go program such as its memory usage, and the frequently called functions to identify the expensive sections of a Go program.

* **Tracing**: Tracing is a way to instrument code to analyze latency throughout the lifecycle of a call or a user request. Traces provide an overview of how much latency each component contributes to the overall latency in a system. Traces can span multiple Go processes.

* **Runtime stats**: Collection and analysis of runtime stats provide a high-level overview of the health of Go programs. Spikes and dips in these values helps us to identify changes in throughput, utilization, and performance.

* **Debugging**: Debugging allows us to pause Go programs and examine its execution. Program state and flow can be verified with debugging.

* **Concurrency**: Concurrency diagnostics tools specialize in addressing concurrency-related verification and sanity check.

Note: The diagnostics tools may interfere with each other. For example, precise memory profiling skews CPU profiles, goroutine blocking profiling affects scheduler trace. Use tools in isolation to get more precise info.

## Profiling

Profiling is useful for identifying expensive or frequently called sections of code. Go runtime provides [profiling data](https://golang.org/pkg/runtime/pprof/) in the format expected by the [pprof visualization tool](https://github.com/google/pprof/blob/master/doc/pprof.md). The profiling data can be collected during testing via `go test` and endpoints made available from the [net/http/pprof](https://golang.org/pkg/net/http/pprof/) package. Users need to collect the profiling data and use pprof tools to filter and visualize the top code paths.

Predefined profiles provided by the [runtime/pprof](https://golang.org/pkg/runtime/pprof/) package:

* **cpu**: CPU profile determines where a program spends its time while actively consuming CPU cycles (as opposed while sleeping or waiting for I/O).

* **heap**: Heap profile reports the currently live allocations; used to monitor current memory usage or check for memory leaks.

* **threadcreate**: Thread creation profile reports the sections of the program that lead the creation of new OS threads.

* **goroutine**: Goroutine profile report the stack traces of all current goroutines.

* **block**: Block profile show where goroutines block waiting on synchronization primitives (including timer channels). Block profile is not enabled by default; use runtime.SetBlockProfileRate to enable it.

* **mutex**: Mutex profile reports the lock contentions. When you think your CPU is not fully utilized due to a mutex contention, use this profile. Mutex profile is not enabled by default, see runtime.SetMutexProfileFraction to enable.

**What other profilers can I use to profile Go programs?**

On Linux, [perf tools](https://perf.wiki.kernel.org/index.php/Tutorial) can be used for profiling Go programs. Perf can profile and unwind cgo/SWIG code and kernel. So it can be useful to get insights into native/kernel performance bottlenecks. On macOS, [Instruments](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/InstrumentsUserGuide/) suite can be used profile Go programs.

**Can I collect pprof profiles from production services?**

You can collect profiling data from running production services but be aware that profiling may affect the overall performance of your running services.

**How can I discover performance and utilization problems of my production services?**

You may want to periodically profile your production services via the pprof [HTTP endpoints](https://golang.org/pkg/net/http/pprof/). Select a production process, profile it for X seconds for every Y seconds and save the results for visualization and analysis; then repeat periodically. Results may be manually and/or automatically reviewed to find problems. Collection of profiles can interfere with each other, it is recommended to collect only a single profile at a time.

**What are the best ways to visualize the profiling data?**

The Go tools provide text, graph, and [callgrind](http://valgrind.org/docs/manual/cl-manual.html) visualization of the profile data via [go tool pprof](https://github.com/google/pprof/blob/master/doc/pprof.md).  Read [Profiling Go programs](https://blog.golang.org/profiling-go-programs) to see them in action. 

Listing of the most expensive calls as text:
![Listing of the most expensive calls as text](http://i.imgur.com/J9yUMVW.png)

Visualization of the most expensive calls as a graph:
![Visualization of the most expensive calls as a graph](http://i.imgur.com/IKF6pqp.png)

Another way to visualize profile data is a [flame graph](https://github.com/uber/go-torch). Flame graphs allow you to move in a specific ancestry path, so you can zoom in/out specific sections of code more easily.

Flame graphs offer visualization to spot the most expensive code-paths:
![Flame graphs offer visualization to spot the most expensive code-paths](http://i.imgur.com/PCLgdct.png)

**Am I restricted to the built-in profiles?**

Additionally to what is provided by the runtime, Go users can create their custom profiles via [pprof.Profile](https://golang.org/pkg/runtime/pprof/#Profile) and use the existing tools to examine them.

**Can I identify whether a specific user/request is responsible for the cost?**

Go will soon allow users to attach [context-scoped labels](https://github.com/golang/proposal/blob/master/design/17280-profile-labels.md) to pprof records. Once profiler labels are available, it will be possible to attach user IDs, request URLs, RPC names, etc. to profiling data which later may be examined by labels.

---

To be continued with tracing, runtime stats, debugging and concurrency sections.