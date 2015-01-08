This page links to resources for learning about server programming in Go. The items are organized into sections by topic.

## Communication

- [Package net/http](http://golang.org/pkg/net/http) provides HTTP client and server implementations.
- [Package encoding/json](http://golang.org/pkg/encoding/json) implements encoding and decoding of JSON objects as defined in RFC 4627.
- [Package net/rpc](http://golang.org/pkg/net/rpc) provides access to the exported methods of an object across a network or other I/O connection.
- [Package os/exec](http://golang.org/pkg/os/exec) runs external commands.
- Read [Go Concurrency Patterns: Context](http://blog.golang.org/context)

## Presentation

- [Package text/template](http://golang.org/pkg/text/template) implements data-driven templates for generating textual output.
- [Package http/template](http://golang.org/pkg/html/template) implements data-driven templates for generating HTML output safe against code injection.

## Profiling and Performance

- Read [Arrays, slices (and strings): The mechanics of 'append'](http://blog.golang.org/slices)
- Read [Profiling Go Programs](http://blog.golang.org/profiling-go-programs)
- [Package runtime/pprof](http://golang.org/pkg/runtime/pprof) writes runtime profiling data in the format expected by the pprof visualization tool.
- [Package net/http/pprof](http://golang.org/pkg/net/http/pprof) serves via its HTTP server runtime profiling data in the format expected by the pprof visualization tool.

## Tracing, Monitoring, Logging, and Configuration

- [Package expvar](http://golang.org/pkg/expvar) provides a standardized interface to public variables, such as operation counters in servers.
- [Package flag](http://golang.org/pkg/flag) implements command-line flag parsing.
- [Package log](http://golang.org/pkg/log) implements a simple logging package.
- [Package glog](https://github.com/golang/glog) implements logging analogous to the Google-internal C++ INFO/ERROR/V setup.

## Storage

- [Package os](http://golang.org/pkg/os) provides a platform-independent interface to operating system functionality.
- [Package path/filepath](http://golang.org/pkg/path/filepath) implements utility routines for manipulating filename paths in a way compatible with the target operating system-defined file paths.
- [Package database/sql](http://golang.org/pkg/database/sql) provides a generic interface around SQL (or SQL-like) databases.

## Platforms

### Google Cloud Platform

- Watch [Go and the Google Cloud Platform](http://blog.golang.org/go-and-google-cloud-platform)
- Read [Go on App Engine: tools, tests, and concurrency](http://blog.golang.org/appengine-dec2013)
- Read [Deploying Go servers with Docker](http://blog.golang.org/docker)
- Search for [App Engine](http://godoc.org/?q=appengine) or [GAE](http://godoc.org/?q=gae) packages

### Amazon Web Services

- [Package goamz](https://wiki.ubuntu.com/goamz) enables Go programs to interact with the Amazon Web Services.
- Search for [AWS](http://godoc.org/?q=aws) packages

### Microsoft Azure

- Microsoft OpenTech's [azure-sdk-for-go](https://github.com/MSOpenTech/azure-sdk-for-go)
- Search for [Azure](http://godoc.org/?q=azure) packages
