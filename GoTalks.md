# Go talks

Check out http://talks.golang.org for presentations for some of the talks. For a comprehensive, curated and searchable index, try [GopherVids](http://gophervids.appspot.com/) from Damian Gryski.

# Official

## Introductory Talks

An introduction to Go.

### Russ Cox's Tour of Go

[[video and discussion](http://research.swtch.com/gotour)]

Three things that make Go fast, fun, and productive:interfaces, reflection, and concurrency. Builds a toy web crawler to demonstrate these.

### Go: a simple programming environment

[[video](http://vimeo.com/53221558)]
[[another video](http://vimeo.com/69237265)]
[[slides](http://talks.golang.org/2012/simple.slide)]

Go is a general-purpose language that bridges the gap between efficient statically typed languages and productive dynamic language. But it’s not just the language that makes Go special – Go has broad and consistent standard libraries and powerful but simple tools.

This talk gives an introduction to Go, followed by a tour of some real programs that demonstrate the power, scope, and simplicity of the Go programming environment.

### Get Started with Go

[[video](http://www.youtube.com/watch?v=2KmHtgtEZ1s)]

Get a feel for the language and its standard libraries and tools in this session, where we go through installing Go and writing some simple but useful
programs.

### Go Programming

[[video](http://www.youtube.com/watch?v=jgVhBThJdXc)] 
[[code](http://talks.golang.org/2010/io/)]

A presentation delivered by Rob Pike and Russ Cox at Google I/O 2010.  It
illustrates how programming in Go differs from other languages through a set of
examples demonstrating features particular to Go.  These include concurrency,
embedded types, methods on any type, and program construction using interfaces.

### The Go Tech Talk

[[video](http://www.youtube.com/watch?v=rKnDgT73v8s)]
[[slides](http://talks.golang.org/2009/go_talk-20091030.pdf)]

An hour-long talk delivered by Rob Pike at Google in October 2009.
The language's first public introduction. The language has changed since it was made,
but it's still a good introduction.

## Development in Go

### Writing Web Apps in Go

[[video](http://www.youtube.com/watch?v=-i0hat7pdpk)] 
[[slides](http://talks.golang.org/2011/Writing_Web_Apps_in_Go.pdf)]

A talk by Rob Pike and Andrew Gerrand presented at Google I/O 2011.
It walks through the construction and deployment of a simple web application
and unveils the [Go runtime for App Engine](http://blog.golang.org/2011/05/go-and-google-app-engine.html).

### Real World Go

[[video](http://www.youtube.com/watch?v=7QDVRowyUQA)] 
[[slides](http://talks.golang.org/2011/Real_World_Go.pdf)]

A talk by Andrew Gerrand presented at Google I/O Bootcamp 2011.
It gives a broad overview of Go's type system and concurrency model
and provides four examples of Go programs that solve real problems.

### Building Integrated Apps on Google's Cloud Platform

[[video](http://www.youtube.com/watch?v=Mo1YKpIF1PQ)]

A talk by Andrew Gerrand presented at Google Developer Day Japan 2011.
It discusses the development of a web application that runs on Google
App Engine and renders raytraced that it stores on Google Cloud Storage.

### High Performance Apps with Go on App Engine

Google I/O, May 2013

[[video](http://www.youtube.com/watch?v=fc25ihfXhbg)] 
[[slides](http://talks.golang.org/2013/highperf.slide)]

### Practical Go Programming

[[video](http://www.youtube.com/watch?v=2-pPAvqyluI)] 
[[slides](http://wh3rd.net/practical-go)] 
[[code](http://github.com/nf/goto)]

This talk presents the development of a complete web application in Go.
It looks at design, storage, concurrency, and scaling issues in detail, using
the simple example of an URL shortening service.

### Lexical Scanning in Go

[[video](http://www.youtube.com/watch?v=HxaD_trXwRE)]

This GTUG talk by Rob Pike discusses the detailed design of a lexical scanner that uses Go's
features in expressive combinations. (The discussion near the end about avoiding goroutines
at initialization is obsolete: Go 1 allows goroutines in init functions so the extra complexity
is unnecessary.)

### Go in Production

Google I/O, June 2012

[[video](http://www.youtube.com/watch?v=kKQLhGZVN4A)]

Since Go's release in 2009 many companies (besides Google, of course) have used the language to build cool stuff. In this session programmers from several companies will share their first-hand experience using Go in production environments.

### Go: code that grows with grace

[[video](http://vimeo.com/53221560)]
[[slides](http://talks.golang.org/2012/chat.slide)]

One of the Go Programming Language’s key design goals is code adaptability; that it should be easy to take a simple design and build upon it in a clean and natural way. In this talk I describe a simple “chat roulette” server that matches pairs of incoming TCP connections, and then use Go’s concurrency mechanisms, interfaces, and standard library to extend it with a web interface and other features. Although the function of the program changes dramatically, the inherent flexibility of Go allows the original design to remain intact as it grows.

### Implementing a bignum calculator

[[video](https://www.youtube.com/watch?v=PXoG0WX0r_E)]
[[slides](http://go-talks.appspot.com/github.com/robpike/ivy/talks/ivy.slide)]

Rob Pike describes his interpreter for an APL-like calculator language.

### Go in Go

[[video](https://www.youtube.com/watch?v=cF1zJYkBW4A)]
[[slides](https://talks.golang.org/2015/gogo.slide)]

Rob Pike speaks on moving the Go toolchain from C to Go

## Concurrency in Go

### Go concurrency patterns

Google I/O, June 2012

[[video](http://www.youtube.com/watch?v=f6kdp27TYZs)]

### Advanced Concurrency Patterns

[[video](https://www.youtube.com/watch?v=QDDwwePbDtw)]
[[slides](http://talks.golang.org/2013/advconc.slide)]

Google I/0, May 2013

Concurrency is the key to designing high performance network services. This talk expands on last year's popular Go Concurrency Patterns talk to dive deeper into Go's concurrency primitives, and see how tricky concurrency problems can be solved gracefully with simple Go code.

## Design of Go

### The Expressiveness Of Go

[[slides](http://talks.golang.org/2010/ExpressivenessOfGo-2010.pdf)]

A discussion of the qualities that make Go an expressive and comprehensible
language.  The talk was presented by Rob Pike at JAOO 2010.
The recording of the event was lost due to a hardware error.

### Another Go at Language Design

[[video](http://sydney.edu.au/engineering/it/videos/seminar_pike) from Sydney University]
[[slides](http://assets.en.oreilly.com/1/event/45/Another%20Go%20at%20Language%20Design%20Presentation.pdf)]

A tour, with some background, of the major features of Go, intended for
an audience new to the language.  The talk was presented at OSCON 2010.
This talk was also delivered at Sydney University in September 2010.

### Go Emerging Languages Conference Talk

[[video](http://confreaks.com/videos/115-elcamp2010-go)]
[[slides](http://assets.en.oreilly.com/1/event/45/Go%20Presentation.pdf)] 

Rob Pike's Emerging Languages Conference presentation delivered in July 2010.  Talk abstract:

> Go’s approach to concurrency differs from that of many languages, even those
> (such as Erlang) that make concurrency central, yet it has deep roots. The path
> from Hoare’s 1978 paper to Go provides insight into how and why Go works as it
> does.

## The State of Go

### June 2014

[[video](https://www.youtube.com/watch?v=0KF44QtoByk)]
[[slides](https://talks.golang.org/2014/state-of-go.slide)]

### February 2015

[[video](https://www.youtube.com/watch?v=Kd8EqTvW5EQ)]
[[slides](https://talks.golang.org/2015/state-of-go.slide)]

### May 2015

[[video](https://www.youtube.com/watch?v=S9Bu6fZnLGM)]
[[slides](https://talks.golang.org/2015/state-of-go-may.slide)]


## Miscellaneous

### The Go frontend for GCC

[[paper](http://talks.golang.org/2010/gofrontend-gcc-summit-2010.pdf)]

A description of the Go language frontend for gcc.
Ian Lance Taylor's paper delivered at the GCC Summit 2010.

### The Go Promo Video

[[video](http://www.youtube.com/watch?v=wwoWei-GAPo)]

A short promotional video featuring Russ Cox demonstrating Go's fast compiler.

### Meet the Go team

Google I/O, June 2012

[[video](http://www.youtube.com/watch?v=sln-gJaURzk)]

A panel discussion with David Symonds, Robert Griesemer, Rob Pike, Ken Thompson, Andrew Gerrand, and Brad Fitzpatrick.

### Fireside Chat with Go team

Google I/0, May 2013

[[video](http://www.youtube.com/watch?v=p9VUCp98ay4)]

A fireside chat with Andrew Gerrand, Brad Fitzpatrick, David Symonds, Ian Lance Taylor, Nigel Tao, Rob Pike, Robert Griesemer, Sameer Ajmani.

### The State of the Gopher

[[video](https://www.youtube.com/watch?v=4KFTacxqkcQ)]
[[slides](https://talks.golang.org/2014/state-of-the-gopher.slide)]

# Unofficial

Talks by members of the community.

### Let's Go, or introduction to Go

[[video (starting at 14:35)](http://live.digicast.ru/view/1582)] 
[[slides](http://talks.godoc.org/github.com/AlekSi/LetsGo/lets-go.slide)] 
[[source](https://github.com/AlekSi/LetsGo)]

This talk gives an introduction to Go in Russian.

### What are Go modules and how do I use them?
_[Paul Jolly](https://twitter.com/_myitcv) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/6MbIzJmLz6Q)]
[[slides](https://talks.godoc.org/github.com/myitcv/talks/2018-08-15-glug-modules/main.slide#1)]

### What else is in Go 1.11
_[Daniel Martì](https://twitter.com/mvdan_) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/mQYjjVCGVJ8)]
[[slides](https://talks.godoc.org/github.com/mvdan/talks/2018/go1.11.slide#1)]

Sneak peak at the Go 1.11 release

### Get Going with WebAssembly
_[Johan Brandhorst](https://twitter.com/JohanBrandhorst) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/iTrx0BbUXI4)]
[[slides](https://talks.godoc.org/github.com/johanbrandhorst/presentations/wasm-lightning/wasm.slide#1)]
[[code wasm](https://github.com/johanbrandhorst/wasm-experiments)]
[[code grpc](https://github.com/johanbrandhorst/grpcweb-wasm-example)]

In this talk, Johan introduces you to the WebAssembly port in Go 1.11 and how it can help when dealing with JavaScript madness :)

### Go and Mongo - and how it's changing
_[DJ Walker-Morgan](https://twitter.com/codepope) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/W22tZ5p3aDk)]
[[slides](https://github.com/codepope/talks/blob/master/GoAndMongo.pdf)]

### Building a simple concurrency teaching language with Go
_[Nicholas Ng](https://twitter.com/nicholascwng) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/7cEp98y6WCs)]
[[slides](https://talks.godoc.org/github.com/nickng/londongophers-aug18/londongophers-aug18.slide#1)]

In this talk Nicholas presents the design and implementation of a simple language designed for teaching concurrency theory (process calculi), implemented in Go. He covers some of Go's static analysis tools used in the implementation and show how you can use them too!

### Introducing Remoto
_[Mat Ryer](https://twitter.com/matryer) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/dhbq7R7h-C0)]

Mat shares the first glimpse of a new project that aims to make building RPC services easy. gRPC isn’t good for clients (especially web), and RESTful designs sometimes lead to confusing APIs. Remoto lets you define your service with a Go interface, and generate everything you need to build and consume the service.

### Go Swagger
_[Simone Trubian](https://twitter.com/simone_trubian) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/PUejMR82RgU)]

Simone gives an overview of the Go Swagger command line tool and briefly explain how he used it to improve productivity in designing REST API's.

### ORMs in Go
_Renato Serra at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/0XW6wI2FnPA)]

Renato explains where ORMs can help, what the options were and what it's been like to use one.

### Unused parameters in Go code
_[Daniel Martì](https://twitter.com/mvdan_) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/VW5jI6V_Y2c)]
[[slides](https://talks.godoc.org/github.com/mvdan/talks/2018/unparam.slide#1)]

Daniel talks about how to use SSA and callgraphs to write powerful code analysis tools. In particular, he demonstrates how to detect unused parameters in functions.

### Lies, Damn Lies, and Benchmarks
_Amnon at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/YDPKUJndhw4)]
[[slides](https://talks.godoc.org/github.com/amnonbc/talks/lies.slide#1)]

Amnon discusses why microbenchmarks can be misleading for optimising real world systems, why data layout is often more significant than code structure, and how Go can help us in the quest for performance.

### A debugger from scratch
_[Liz Rice](https://twitter.com/LizRice) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/tZ5PUKbGjO4)]
[[slides](https://speakerdeck.com/lizrice/debuggers-from-scratch)]
[[code](https://github.com/lizrice/debugger-from-scratch)]

Liz explains how a debugger works by building one in a few lines of Go. This includes mapping between Go source code and the machine code instructions it compiles to, and using the ptrace system call to set break points and examine and modify the running process.

### Fast Fractal Fun With SDL
_[Sue Spence](https://twitter.com/virtualsue) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/eTjL3grAYAM)]
[[slides](https://gitlab.com/virtualsue/sdl-fractal/blob/master/Fast%20Fractal%20Fun.pdf)]
[[code](https://gitlab.com/virtualsue/sdl-fractal)]

Go programs which create images such as the Mandelbrot & Julia sets often output an image file. I will show how to use Go bindings for the Simple Directmedia Layer library to output them on a display device instead.

### Concurrency: a Journey from Ruby to Go
_[Mathilda Thompson](https://twitter.com/mathildathompso) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/mK3r5PDED-0)]

### Go in a Polyglot Environment
_[Kevin McKelvin](https://twitter.com/kmckelvin) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/kWAxBhsEayk)]

In this talk Kevin goes through his experience of adopting Go, moving to a polyglot environment, successes and challenges, and how Go fits into his company's overall architecture and strategy.

### Delivering Go Services
_[Zak Knill](https://twitter.com/zakknill) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/pRdfJTuGxEw)]

Delivering Go Services: After introducing Go to your company, and deploying your first go service. What are the next steps? This talk focuses on some of the things that come next, touching on the fabled "New service to prod in X (10, 20, 30) mins", as well as some gotchas along the way.

### Go-ing Lambda

_[David Blooman](https://twitter.com/dblooman) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/BBiIr19JOo4)]

Go-ing Lambda - A year in production: How we(FundApps) used Go in lambda functions to build a service for importing/scraping/parsing data for financial services to build API's on top of. Tips and tricks of lambda functions in Go, limitations, performance and using the Apex framework.

### The RED method

_[Tom Wilkie](https://twitter.com/tom_wilkie) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/rc3V-k-JYAo)]

We'll also have a section dedicated to those of you who are hiring or looking to get hired (if we'll miss it like last time, please don't be afraid to remind us).

### Abusing Go’s net package for fun and profit
_[Michał Witkowski](https://twitter.com/MWitkow) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/JDjHFmke0ZI)]

This talks into the details of how Go’s composition-based philosophy, as applied to the net package, can be creatively leveraged to beautiful and useful hacks that significantly augment the functionality of the stack. We’ll explore the net.Conn, and how one can (ab)use them in creative ways. We’ll take a peek into net/http, and explore how the http.Handler and http.Roundtripper interfaces can be creatively appropriated to build useful middleware. We’ll then dig even deeper into the net/http internals and how they related tls.Conn and x/net/http2, to understand how they work, and armed with that knowledge we’ll demonstrate some of our most beautiful hacks.

### 2018's stringer
_[Daniel Martì](https://twitter.com/mvdan_) at [**LondonGophers**](https://twitter.com/LondonGophers)_

[[video](https://youtu.be/IyVEW19IkXE)]
[[slides](https://talks.godoc.org/github.com/mvdan/talks/2018/stringer.slide)]

2018's stringer - a demonstration of new features you likely haven't heard of.