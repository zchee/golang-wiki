This page links to resources for learning about server programming in Go - both web services and mobile backends. The items are organized into sections by topic.

## Getting Started

- Read [Writing Web Applications with the Go standard library](http://golang.org/doc/articles/wiki/)
- Read [Build a Web Application With Go](https://www.gitbook.com/book/astaxie/build-web-application-with-golang/details) from the author of the [BeeGo web framework](http://beego.me/)
- Read [Webapps in Go the anti textbook](https://github.com/thewhitetulip/web-dev-golang-anti-textbook)
- Read [Building Web Applications in Go](https://www.gitbook.com/book/codegangsta/building-web-apps-with-go/details) from the author of the [Negroni](https://github.com/codegangsta/negroni) and [Martini](http://martini.codegangsta.io/) webserver toolkits. First learn the absolute basics before going to this book.
- Read [Building Your Own Web Framework in Go](https://www.nicolasmerouze.com/build-web-framework-golang/) a 5-part series.
- Watch [Go: code that grows with grace](http://talks.golang.org/2012/chat.slide#1)
- Download a [full working 3-tier application example](https://github.com/sourcegraph/thesrc) from the Sourcegraph Team.

### Middleware

A topic you will see discussed frequently is "middleware". If you're not familiar with that term, we suggest you start out by reading a few of these articles:

* [Writing Handsome Golang Middleware](http://laicos.com/writing-handsome-golang-middleware/) _2015-05-05_
* [Middleware in Go: Best practices and examples](https://www.nicolasmerouze.com/middlewares-golang-best-practices-examples/) _2014-11-13_
* Custom Handlers [Part 1 - Avoiding Globals](http://elithrar.github.io/article/custom-handlers-avoiding-globals/), [Part 2 - Error Handling](http://elithrar.github.io/article/http-handler-error-handling-revisited/) _2014-07-16_
* [Making and Using HTTP Middleware](http://www.alexedwards.net/blog/making-and-using-middleware) _2014-10-21_
* [Writing HTTP Middleware in Go](https://justinas.org/writing-http-middleware-in-go/) _2013-10-09_


## Toolkits and Frameworks

Before you decide to adopt a third party web framework or toolkit, keep in mind that the Go standard library provides all of the tools you need to build a sophisticated, modern web application. Keeping with Go's preference for simplicity and composability over complexity and magic, we suggest you [see how far the standard library can take you](http://golang.org/doc/articles/wiki/).

If you decide you need a bit more infrastructure, start by looking at some of the toolkits and libraries available.

### Toolkits & Libraries & Microframeworks

* [Gorilla Toolkit](http://www.gorillatoolkit.org/)
* [Negroni Toolkit - Idiomatic HTTP Middleware for Go](https://github.com/codegangsta/negroni)
* [Echo Framework - Fast and Unfancy](http://echo.labstack.com/)
* [Goji Web Microframework](https://goji.io/)
* [Go Craft Middleware](https://github.com/gocraft/web)
* [Go RESTful](https://github.com/emicklei/go-restful) - Toolkit for RESTful service APIs
* [limiter](https://github.com/ulule/limiter) - Simple rate-limiting middleware for Go
* [Kite Micro-service framework](https://github.com/koding/kite)
* [Alice - Painless middleware chaining for Go](https://github.com/justinas/alice)
* [YAM - Yet Another Mux](https://github.com/thisissoon/yam)
* [Bone - Fast HTTP Router](http://go-zoo.github.io/bone/)

### Frameworks

* [BeeGo Framework](http://beego.me/)
* [Frodo](https://github.com/kn9ts/frodo) - Go mini web framework inspired by Laravel(php), Slim(php) and ExpressJS(node.js)
* [GinGonic](https://gin-gonic.github.io/gin/)
* [Macaron](https://github.com/Unknwon/macaron) - Productive, modular web framework in Go.
* [Revel Web Framework](https://revel.github.io/)
* [Ringo](https://github.com/jjyr/ringo) - Lightweight MVC web framework inspired by Rails, Gin.
* [Utron](https://github.com/gernest/utron) - Lightweight MVC framework for web applications.
* [Iris](https://github.com/kataras/iris/) - Fast MVC framework for web applications.

## Communication

- [Package net/http](http://golang.org/pkg/net/http) provides HTTP client and server implementations.
- [Package encoding/json](http://golang.org/pkg/encoding/json) implements encoding and decoding of JSON objects as defined in RFC 4627.
- [Package net/rpc](http://golang.org/pkg/net/rpc) provides access to the exported methods of an object across a network or other I/O connection.
- [Package os/exec](http://golang.org/pkg/os/exec) runs external commands.

## Presentation

- [Package text/template](http://golang.org/pkg/text/template) implements data-driven templates for generating textual output.
- [Package html/template](http://golang.org/pkg/html/template) implements data-driven templates for generating HTML output safe against code injection.

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

- Read [Go, Cloud Endpoints and App Engine, Part 1](https://medium.com/google-cloud/go-cloud-endpoints-and-app-engine-19d290dafda3), [Part 2](https://medium.com/@IndianGuru/go-cloud-endpoints-and-app-engine-e3413c01c484)
- Read [Google Cloud Platform: Go Runtime Environment](https://cloud.google.com/appengine/docs/go/)
- Watch [Go and the Google Cloud Platform](http://blog.golang.org/go-and-google-cloud-platform)
- Read [Go on App Engine: tools, tests, and concurrency](http://blog.golang.org/appengine-dec2013)
- Get [Google Cloud Platform Go Libraries](http://godoc.org/google.golang.org/cloud)
- Read [Deploying Go servers with Docker](http://blog.golang.org/docker)
- Search packages for [Google Cloud](http://godoc.org/?q=google+cloud) or [gcloud](http://godoc.org/?q=gcloud)
- Search packages for [App Engine](http://godoc.org/?q=appengine) or [GAE](http://godoc.org/?q=gae)

### Amazon Web Services

- The [aws-sdk-go](https://github.com/aws/aws-sdk-go) repository provides automatically generated AWS clients in Go.  It has [official support](https://aws.amazon.com/blogs/aws/now-available-version-1-0-of-the-aws-sdk-for-go/) from Amazon.
- [Package goamz](https://wiki.ubuntu.com/goamz) enables Go programs to interact with the Amazon Web Services.
- Search packages for [AWS](http://godoc.org/?q=aws) or [Amazon services](http://godoc.org/?q=amazon+service)

### Microsoft Azure

- Microsoft OpenTech's [azure-sdk-for-go](https://github.com/MSOpenTech/azure-sdk-for-go) provides a Golang package that makes it easy to consume and manage Microsoft Azure Services.
- Search packages for [Azure](http://godoc.org/?q=azure)

### Openstack / Rackspace

- [Gophercloud](https://github.com/gophercloud/gophercloud) is a Golang SDK for working with OpenStack clouds.
- Search packages for [Openstack](http://godoc.org/?q=openstack) or [Rackspace](http://godoc.org/?q=rackspace)

### IBM BlueMix

- [Write your first Golang app on BlueMix](https://developer.ibm.com/bluemix/2015/10/28/getting-started-with-golang-on-bluemix/)
