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