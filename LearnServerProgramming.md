This page links to resources for learning about server programming in Go. The items are organized into sections by topic.

## Getting Started

- Code [A Tour of Go: Web Servers](http://tour.golang.org/methods/13) and [HTTP Handlers](http://tour.golang.org/methods/14)
- Read [Writing Web Applications](http://golang.org/doc/articles/wiki/)
- Read [LearnConcurrency](/golang/go/wiki/LearnConcurrency)
- Watch [Go: code that grows with grace](http://talks.golang.org/2012/chat.slide#1)

## Communication

- [Package net/http](http://golang.org/pkg/net/http) provides HTTP client and server implementations.
- [Package encoding/json](http://golang.org/pkg/encoding/json) implements encoding and decoding of JSON objects as defined in RFC 4627.
- [Package net/rpc](http://golang.org/pkg/net/rpc) provides access to the exported methods of an object across a network or other I/O connection.
- [Package os/exec](http://golang.org/pkg/os/exec) runs external commands.

## Presentation

- [Package text/template](http://golang.org/pkg/text/template) implements data-driven templates for generating textual output.
- [Package http/template](http://golang.org/pkg/html/template) implements data-driven templates for generating HTML output safe against code injection.

## Profiling and Performance

- Read [Profiling Go Programs](http://blog.golang.org/profiling-go-programs)
- Read [Arrays, slices (and strings): The mechanics of 'append'](http://blog.golang.org/slices)
- Read the [Frequently Asked Questions (FAQ)](http://golang.org/doc/faq), especially
    - [Why does Go perform badly on benchmark X?](http://golang.org/doc/faq#Why_does_Go_perform_badly_on_benchmark_x)
    - [Why do garbage collection? Won't it be too expensive?](http://golang.org/doc/faq#garbage_collection)
- [Package bufio](http://golang.org/pkg/bufio) implements buffered I/O.
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

- Read [Google Cloud Platform: Go Runtime Environment](https://cloud.google.com/appengine/docs/go/)
- Watch [Go and the Google Cloud Platform](http://blog.golang.org/go-and-google-cloud-platform)
- Read [Go on App Engine: tools, tests, and concurrency](http://blog.golang.org/appengine-dec2013)
- Read [Deploying Go servers with Docker](http://blog.golang.org/docker)
- Search packages for [Google Cloud](http://godoc.org/?q=google+cloud) or [gcloud](http://godoc.org/?q=gcloud)
- Search packages for [App Engine](http://godoc.org/?q=appengine) or [GAE](http://godoc.org/?q=gae)

### Amazon Web Services

- [Package goamz](https://wiki.ubuntu.com/goamz) enables Go programs to interact with the Amazon Web Services.
- Search packages for [AWS](http://godoc.org/?q=aws) or [amazon services](http://godoc.org/?q=amazon+service)

### Microsoft Azure

- Microsoft OpenTech's [azure-sdk-for-go](https://github.com/MSOpenTech/azure-sdk-for-go) provides a Golang package that makes it easy to consume and manage Microsoft Azure Services.
- Search packages for [Azure](http://godoc.org/?q=azure)
