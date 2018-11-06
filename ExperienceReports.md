This page collects experience reports about problems with Go that might inform our design of solutions to those problems. These reports should focus on the _problems_: they should not focus on and need not propose solutions. To propose solutions, see the [proposal process](https://golang.org/s/proposal). 

We hope to use these experience reports to understand where people are having trouble writing Go, to help us prioritize future changes to the Go ecosystem.  (We do not promise to reply to these. If you need immediate help answering questions about Go, see [https://golang.org/help/](https://golang.org/help/) for resources.)

__The best experience reports tell: (1) what you wanted to do, (2) what you actually did, and (3) why that wasn’t great, illustrating those by real concrete examples, ideally from production use.__ Please write these reports about the problems most significant to you, post them on your own blog, or on Medium, or as a [Github Gist](https://gist.github.com/) (use a `.md` extension for Markdown), or as a publicly-readable Google doc, and then link them here. (Talk videos or slides are also welcome, although they are not as convenient for us to digest.)

If you do not have permission to edit the wiki to add an article to this list, [please file an issue](https://golang.org/issue/new).

Please keep the overall page sorted alphabetically by section (Error Handling before Logging, and so on).
Within a section, please keep articles sorted chronologically.
It's helpful to include a one-phrase summary of the point of each article.

Add new sections as appropriate.

**Table of Contents**

  - [App and Game Development](#app-and-game-development)
  - [Concurrency](#concurrency)
  - [Casting](#casting)
  - [Context](#context)
  - [Declarations](#declarations)
  - [Dependencies](#dependencies)
  - [Documentation](#documentation)
  - [Diagnostics and Debugging](#diagnostics-and-debugging)
  - [Education and Teaching](#education-and-teaching)
  - [Error Handling](#error-handling)
  - [File System](#file-system)
  - [Generics](#generics)
  - [GoMobile](#gomobile)
  - [Immutability](#immutability)
  - [Inter Process Communication](#inter-process-communication)
  - [Large-Scale Software Development](#large-scale-software-development)
  - [Logging](#logging)
  - [Misc/Multiple](#misc--multiple)
  - [Modules](#modules)
  - [Performance](#performance)
  - [Porting](#porting)
  - [Slices](#slices)
  - [Syntax](#syntax)
  - [Time](#time)
  - [Tooling](#tooling)
  - [Type System](#type-system)
  - [Typed nils](#typed-nils)
  - [Vendoring](#vendoring)

## App and Game Development

  - Paul Ruest, "[Go Library Support for Apps and Games](https://gazed.github.io/goApps.html)", November 2017
  - Tad Vizbaras, "[Building Optical Character Recognition (OCR) in Go](http://recoink.com/goreport)", December 2017

## Casting
  - Richard Warburton, "[Should Go Casting be permitted when underlying data structures are the same?](https://gist.github.com/krolaw/f010ab0966fd379725ecc48e8bbcac1c)", December 2017

## Concurrency

  - Sergey Kamardin, “[A Million WebSockets and Go](https://medium.freecodecamp.org/million-websockets-and-go-cc58418460bb),” August 2017, about the memory overhead of blocked read/write goroutines.
  - Nathaniel J. Smith, “[Notes on structured concurrency, or: Go statement considered harmful](https://vorpus.org/blog/notes-on-structured-concurrency-or-go-statement-considered-harmful/)”, April 2018.

## Context

  - Sam Vilain, “[Using Go's context library for making your logs make sense](https://blog.gopheracademy.com/advent-2016/context-logging/),” December 2016, about extracting structured log values from context.
  - Jon Calhoun, “[Pitfalls of context values and how to avoid or mitigate them in Go](https://www.calhoun.io/pitfalls-of-context-values-and-how-to-avoid-or-mitigate-them/),” February 2017.
  - Michal Štrba, "[Context should go away for Go 2](https://faiface.github.io/post/context-should-go-away-go2/)," August 2017
  - Axel Wagner, "[Why context.Value matters and how to improve it](https://blog.merovius.de/2017/08/14/why-context-value-matters-and-how-to-improve-it.html)," August 2017.
  - Dave Cheney, "[Context isn't for cancellation](https://dave.cheney.net/2017/08/20/context-isnt-for-cancellation)," August 2017.
  - Ross Light, "[Canceling I/O in Go Cap'n Proto](https://medium.com/@zombiezen/canceling-i-o-in-go-capn-proto-5ae8c09c5b29)," January 2018.
  - Iman Tumorang, "[Avoiding Memory Leak in Golang API](https://hackernoon.com/avoiding-memory-leak-in-golang-api-1843ef45fca8)," January 2018.

## Declarations

  - Christophe Meessen, "[Problems with Go's shorthand declaration :=](https://gist.github.com/chmike/ac0113afefbc04e67323b4a3688d6b54#file-godeclareproblem-md)", July 2017, about the shadowing var trap and apparent inconsistency of `:=`. 
  - Brian Will, "[Go's := syntax is error-prone with multiple target variables](https://gist.github.com/BrianWill/671ce51e6ef6a9f0caa27272a9a0637f)", August 2017.

## Dependencies

  - John Doe, "[Forks, import paths, and `go get`](https://gist.github.com/johnAnonDoe/2071b8811300c6c08ac21cc8da9fa4d3)", July 2017.
  - Patrick Bohan, "[Docker => Moby: Go Dependencies](http://engineering.rallyhealth.com/go/golang/dependencies/package-managers/2017/06/28/go-and-dependencies.html)," Jun 28, 2017. A new Go team's struggles with dependency management and an approach to deal with them.
  - Judson Lester, "[untitled gist] (https://gist.github.com/nyarly/edb6b7a5e3a762da6a5e2da8f59acf07)", August 2017.
  - David Collier-Brown, "[Avoiding an NP-Complete Problem by Recycling Multics’ Answer](https://leaflessca.wordpress.com/2018/09/03/avoiding-an-np-complete-problem-by-recycling-multics-answer/)", September 2018.

## Diagnostics and Debugging

  - Kevin Burke, "[How I'm running benchmarks and printing their results](https://github.com/kevinburke/go-html-boilerplate/blob/master/Makefile#L38)", it would be nice if I didn't need so much Unix glue to run and print these. July 2017.

  - John Clarke, Tracking down an intermittent fault (not a race) by running a very slow {hit test failure, increase logging} cycle by running "do { go test -race } while ( $LASTEXITCODE -eq 0 )" overnight. Over many nights. Execution trace functionality like https://rr-project.org/ would be transformative.  November 2018.  

## Education and Teaching

  - Carl Kingsford and Phillip Compeau, "[Go 2.0 for Teaching](http://www.monogrammedchalk.com/go-2-for-teaching/)". Experience using Go in an introductory programming course.

## Documentation

  - Kevin Burke, "[Need to add documentation for a binary in three different places](https://github.com/golang/go/issues/20212)", May 2017.

## Error Handling

(This section is about writing `if err != nil`.)

  - Andrew Gerrand, “[Error Handling and Go](https://blog.golang.org/error-handling-and-go),” July 2011,
    showing Go error handling patterns.
  - Martin Sústrik, “[Why should I have written ZeroMQ in C, not C++ (part I)](http://www.250bpm.com/blog:4),” May 2012,
    discussing production problems with C++ exception handling due to error-handling code being far from code that causes the error.
  - Thomi Richards, “[The Problems with Errors](http://www.tech-foo.net/the-problems-with-errors.html),” March 2014,
    arguing that it's essential for code to document exactly which errors it returns / exceptions it might throw.
  - Roger Peppe, “[Lovin' your errors](https://rogpeppe.neocities.org/error-loving-talk/index.html),” March 2015, discussing idioms for error handling.
  - Bleve, “[Deferred Cleanup, Checking Errors, and Potential Problems](http://www.blevesearch.com/news/Deferred-Cleanup,-Checking-Errors,-and-Potential-Problems/),” September 2015,
    showing a bug related to error handling and defer in Bleve search.
  - Andrew Morgan, “[What I Don't Like About Error Handling in Go, and How to Work Around It](https://opencredo.com/why-i-dont-like-error-handling-in-go/),” January 2017,
    about it being difficult to force good error handling, errors not having stack traces, and error handling being too verbose.
  - André Hänsel, "[If Ⅰ were to make my own Go…](https://blog.creations.de/?p=223)", August 2017
  - Peter Goetz, "[Thinking About New Ways of Error Handling in Go 2](https://medium.com/@peter.gtz/thinking-about-new-ways-of-error-handling-in-go-2-e56d116952f1)," September 2017, shows how error-prone error handling in Go is and lays out requirements to improve the experience.

## Error Values

(This section is about additional error semantics beyond the `Error() string` method.)

  - Andrew Morgan, “[What I Don't Like About Error Handling in Go, and How to Work Around It](https://opencredo.com/why-i-dont-like-error-handling-in-go/),” January 2017,
    about it being difficult to force good error handling, errors not having stack traces, and error handling being too verbose.
  - Chris Siebenmann, “[Go's net package doesn't have opaque errors, just undocumented ones](https://utcc.utoronto.ca/~cks/space/blog/programming/GoNetErrorsUndocumented),” August 2018

## File System

  - Chris Lewis, “[Non-Local File Systems Should Be Supported](https://gist.github.com/cflewis/87843028576459b0f6ebf55f1b200891),” July 2017. Proposes replacing file system read calls to something more abstracted like the `sql` package does.

## Generics

  - “[Summary of Go Generics Discussions (living document)](https://docs.google.com/document/d/1vrAy9gMpMoS3uaVphB32uVXX4pi-HnNjkMEgyAHX4N4/edit).”
  - Bouke van der Bijl, “[Idiomatic Generics in Go](https://web.archive.org/web/20141001043016/http://bouk.co/blog/idiomatic-generics-in-go/),” September 2014.
  - Craig Weber, “[Living without generics in Go](https://web.archive.org/web/20141227092139/http://www.weberc2.com/posts/2014/12/12/living-without-generics.txt),” December 2014.
  - Shashank Sharma, “[Poor man's generics in Golang (Go)](https://codeblog.shank.in/poor-mans-generics-in-golang/),” May 2016.
  - Niek Sanders, “[Overhead of Go's generic sort](https://github.com/nieksand/sortgenerics),” September 2016,
    documenting the overhead of sorting using sort.Interface instead of specialized code.
  - Jon Calhoun, “[Using code generation to survive without generics in Go](https://www.calhoun.io/using-code-generation-to-survive-without-generics-in-go/),” May 2017.
  - Jon Bodner, “[Closures are the Generics for Go](https://medium.com/capital-one-developers/closures-are-the-generics-for-go-cb32021fb5b5),” June 2017.
  - Andrew Stock, "[Why I miss generics in Go](https://medium.com/@watchforstock/why-i-miss-generics-in-go-9aef810a1bef)," June 2017
  - Kevin Burke, "[Code example with lots of interface casts](https://gist.github.com/kevinburke/a10aed6d8d07ecd5efe658b21cd168c1)," requires a lot of boilerplate/casts.
  - Ian Lance Taylor, "[The append function](https://www.airs.com/blog/archives/559)," July 2017.
  - DeedleFake, "[The Problem with Interfaces](https://deedlefake.com/2017/07/the-problem-with-interfaces/)", July 2017.
  - Kurtis Nusbaum "[Why I'm So Frustrated With Go](https://hackernoon.com/why-im-so-frustrated-with-go-97c0c4ae214e)," June 2017
  - Juan Álvarez, "[Generics on Go's stdlib](https://medium.com/@shixzie/generics-on-gos-stdlib-10de52fe824d)", July 2017.
  - David Chase, "[A use case for Go Generics in a Go Compiler](https://dr2chase.wordpress.com/2017/08/09/a-use-case-for-go-generics-in-a-go-compiler/)", August 2017
  - Varun Kumar, "[Generics - I Wish You Were Here...](https://varunksaini.com/blog/use-case-for-generics/)", August 2017
  - Sameer Ajmani, "[Go Experience Report for Generics: Google metrics API](https://medium.com/@sameer_74231/go-experience-report-for-generics-google-metrics-api-b019d597aaa4)", August 2017
  - Chewxy, "[Tensor Refactor: A Go Experience Report](https://blog.chewxy.com/2017/09/11/tensor-refactor/)", September 2017, discusses the lack of generics and how it affects building high performance multidimensional arrays for different data types (having to resort to a lot of pointer ugliness, and manually keeping track of type and runtime type checking)
 - qwerty2501,"[A problem runtime error due to lack of Generics](https://gist.github.com/qwerty2501/8839af87946571943a6c4f623c6124e2)", October 2017
 - posener, "[Why I recommend to avoid using the go-kit library](https://gist.github.com/posener/330c2b08aaefdea6f900ff0543773b2e)", clear separation of concern need lots of boilerplate code. gokit try 
code generation to avoid this [#70](https://github.com/go-kit/kit/issues/70) [#308](https://github.com/go-kit/kit/pull/308) [protoc-gen-gokit](https://github.com/AmandaCameron/protoc-gen-gokit) , but it looks like
a complex solution for the problem. 
 - Xavier Leroy, "[A modular module system](http://gallium.inria.fr/%7Exleroy/publi/modular-modules-jfp.pdf)", paper about module description for generics.
 - Tobias Gustafsson, "[Experiences implementing PEDS](https://github.com/tobgu/peds/blob/master/experience_report.md)", PEDS is a set of statically type safe, immutable/persistent, collections. November 2017
 - A Googler "[govisor/generics.go](https://github.com/google/gvisor/blob/master/tools/go_generics/generics.go)". April 27, 2018

## GoMobile
 - Vijay, "[Nested structs and slices not supported in gomobile]"

## Immutability
  - Kurtis Nusbaum "[Why I'm So Frustrated With Go](https://hackernoon.com/why-im-so-frustrated-with-go-97c0c4ae214e)," June 2017
 - Sindre Myren "[Go 2.0: Retain simplicity by trading features](https://medium.com/@smyrman/go-2-0-retain-simplicity-by-trading-features-b310b60862ea)" July 2017
 - Tobias Gustafsson, "[Experiences implementing PEDS](https://github.com/tobgu/peds/blob/master/experience_report.md)", PEDS is a set of statically type safe, immutable/persistent, collections. November 2017

## Inter Process Communication
  - Pablo R. Larraondo "[A Go interprocess communication model](https://gist.github.com/prl900/a7aaa41707e2236592da5e78d8a10dc9)," August 2017

## Large-Scale Software Development
  - Russ Cox, “[Codebase Refactoring (with help from Go)](https://talks.golang.org/2016/refactor.article),” November 2016, laying out the gradual code repair problem addressed in part by type aliases ([#18130](https://golang.org/issue/18130)).

## Logging

  - Evan Miller, “[Logging can be tricky](http://corner.squareup.com/2014/09/logging-can-be-tricky.html),” September 2014,
    showing how logging can add to application tail latency.
  - Dave Cheney, “[Let's talk about logging](https://dave.cheney.net/2015/11/05/lets-talk-about-logging),” November 2015,
    arguing that there are only two log levels.
  - TJ Holowaychuk, “[Apex log](https://medium.com/@tjholowaychuk/apex-log-e8d9627f4a9a),” January 2016, describing a structured log package and how it would be used in production.
  - Paddy Foran, “[Logging in Go](http://tech.dramafever.com/golang/2016/02/08/logging-in-go),” February 2016, showing how DramaFever sends Go program logs to Sentry.
  - Martin Angers, “[About Go logging for reusable packages](https://www.0value.com/about-go-logging),” March 2016, making suggestions for how to write code that doesn't assume a particular log package.
  - BugReplay.com, “[How to use Google Cloud's Free Structured Logging Service With Golang](http://blog.bugreplay.com/post/150086459149/how-to-use-google-clouds-free-structured-logging),” September 2016.
  - Sam Vilain, “[Using Go's context library for making your logs make sense](https://blog.gopheracademy.com/advent-2016/context-logging/),” December 2016, about extracting structured log values from context.
  - Logmatic, “[Our Guide to a Golang Logs World](https://logmatic.io/blog/our-guide-to-a-golang-logs-world/),” March 2017.
  - Chris Hines, Peter Bourgon, “[Proposal: standard Logger interface](https://docs.google.com/document/d/1shW9DZJXOeGbG9Mr9Us9MiaPqmlcVatD_D8lrOXRNMU/edit?usp=drive_web),“ February 2017, problems related to stdlib logger, especially in the context of libraries, and one proposed solution.
  - Sindre Myren, "[There is nothing Goish about log.Fatal](https://medium.com/@smyrman/there-is-nothing-goish-about-log-fatal-4ab24ae5ba7)" August 2017, how poorly log.Fatal plays with defer, and a simple pattern for delaing with it in Go 1.x and Go 2.x.

## Misc / Multiple
  - Iman Tumorang, "[Trying Clean Architecture on Golang](https://hackernoon.com/golang-clean-archithecture-efd6d7c43047)" July 2017
  - Laurent Demailly, "[My Go lang experience, part 1](https://laurentsv.com/blog/2017/12/28/about-golang.html)" December 2017, a laundry list of pros and cons with current Go from an experienced C/C++/Java/Scripting languages developer perspective.
  - Gokcehan Kara, "[Installation with Go Language can be Simpler](https://gokcehan.github.io/posts/installation-with-go-language-can-be-simpler.html)" May 2018, some complications about the installation and distribution of static stripped binaries with version information.
  - Bob Nystrom, "[The Language I Wish Go Was](https://journal.stuffwithstuff.com/2010/10/21/the-language-i-wish-go-was/)" October 2010, I wish Go had tuples, unions, constructors, no Nil, exceptions, generics, some syntax sugar, and ponies that shoot Cheez Whiz out of their noses.

## Modules
  - Paul Jolly - "[Creating a submodule within an existing module](https://gist.github.com/myitcv/79c3f12372e13b0cbbdf0411c8c46fd5)" - covers multi-module repos, cyclic module dependencies and the steps required to move between various "states"

## Performance

  - Kevin Burke, "[Real Life Go Benchmarking](https://kev.inburke.com/kevin/real-life-go-benchmarking/)," trying to explain to the average developer how to use tools like pprof, maybe this could be easier. July 2016.
  - Nathan Kerr, "[Concurrency Slower?](https://pocketgophers.com/concurrency-slower/)", shows how to use Go's testing, benchmarking, and profiling tools to improve the performance of a concurrent implementation of a function. April 2017.

## Porting
  - Shannon Pekary, "[Why GOPP](https://github.com/spekary/gopp/blob/master/Why.md)," an attempt to create 
a 'class' keyword that simply makes a struct to also be an interface to make porting code from object-oriented languages much easier.

## Slices
  - Richard Warburton, "[Should Go 2.0 support slice comparison?](https://gist.github.com/krolaw/3205a3139d423b0c39e24b98c923b1a1)," an argument to treat slices as structs for equality comparison, ignoring backing arrays.
  - "[Deduplicating a slice is too cumbersome](https://gist.github.com/kevinburke/ad20587e6694acb9251f7d7e25c77078)," a 10-line function in your source code vs. e.g. Ruby's `uniq` function.
  - "[Counter-intuitive behaviour of Go variadic functions](https://gist.github.com/dpinela/f7fdeb0ce3e1f0b4f495917ad9210a85),", January 2018, stumbling blocks encountered when expanding slices into argument lists.

## Syntax
  - André Hänsel, "[If Ⅰ were to make my own Go…](https://blog.creations.de/?p=223)", August 2017

## Time 

  - John Graham-Cumming, “[How and Why the Leap Second Affected Cloudflare DNS](https://blog.cloudflare.com/how-and-why-the-leap-second-affected-cloudflare-dns/),” January 2017, about timing across leap seconds ([#12914](https://golang.org/issue/12914)).

## Tooling

  - Jonathan Ingram, “[gofmt is not opinionated enough](https://gist.github.com/jonathaningram/2b62022844348f3407518dd3a180ef42)”, August 2017, about ongoing debates between developers regarding code style because `gofmt` is not opinionated enough.
  - Jean-Laurent de Morlhon, "[Pourquoi Maurice ne doit surtout pas coder en GO](https://www.youtube.com/watch?v=LIFZPzupwgs), talk about Go from a java developper perspective ("go dep" is not enough,...), slides are in english.

## Type System

  - Sam Whited, “[Faking Enumeration Types with Consts and Unexported Types](https://gist.github.com/SamWhited/6cdbc49b4562e1a1b0526af523f5c5d7)”, July 2017, about attempting to ensure compile time correctness of values provided to an API using the type system.
  - Andreas Matuschek, "[Operator Methods](https://gist.github.com/maj-o/9cab355e3e5e4f6f66dbf0a8f24cd13a)", July 2017, just to remember that there are problems with types without corresponding operators ([#19770](https://github.com/golang/go/issues/19770)).
  - Leigh McCulloch, "[Go Experience Report: Pointers](https://leighmcculloch.com/go-experience-reports/pointers.html)", July 2017, about pointers being used for both transferring ownership and indicating a lack of value.
  - Jack Lindamood, "[Interface wrapping method erasure](https://medium.com/@cep21/interface-wrapping-method-erasure-c523b3549912)", July 2017, about the loss of information due to type wrappers
- Sam Whited, “[The Case for interface{}](https://blog.samwhited.com/2017/08/the-case-for-interface/)”, Aug 2017, two examples of using interface and why one is bad (but necessary) and one is good.
- James Frasché, "[Sum types experience report](https://gist.github.com/jimmyfrasche/ba2b709cdc390585ba8c43c989797325)", Aug 2017, issues caused by inability to restrict to a closed set of types
- Robin Eklind, "[Specific use cases. In response to James Frasché's 'Sum types experience report'](https://gist.github.com/jimmyfrasche/ba2b709cdc390585ba8c43c989797325#gistcomment-2181410)", Aug 2017, issues caused by inability to restrict to a closed set of types
- Rick Branson, "[Implicit Pointers = Explicitly Bad](https://docs.google.com/document/d/1va7f4YvExK4mNBmMt2RMg1SNSHyljc8ARVp2ATKtBwU/edit?usp=sharing)", Sep 2017, issues encountered with parameters/variables with interface types as implicit references
- Chewxy, "[Tensor Refactor: A Go Experience Report](https://blog.chewxy.com/2017/09/11/tensor-refactor/)", September 2017, issues regarding discussion of a type system in Go
- Walter Schulze, "[Generic functions cannot be passed as values](https://gist.github.com/awalterschulze/e3999f8cfa29b246c35a651a2be4d121)", September 2017
- Walter, Schulze, "[For Sum Types: Multiple return parameters are overrated](https://awalterschulze.github.io/blog/post/sum-types-over-multiple-returns/)", September 2017
- Nicolas, Boulay "[Sum type not always the best choice (Typed tagless-final interpretations)](https://gist.github.com/nicolasboulay/a8ee4a65e8c2cc110c20e6d24e838e86), October 2017
- Eduard Urbach, "[Type-casting interface{} to chan interface{}](https://github.com/blitzprog/go-channel-type-casting)", October 2017
- David Vennik, "[Unjumbling Golang OOP primitives](https://gist.github.com/l0k1verloren/344956daedb434094e9af2c21ff9376c)", April 20, 2018 - The problem of the lack of structuring in OOP primitives - dummy functions and redundant boilerplate type bindings.
- Jelte Fennema, "[Fixing the billion dollar mistake in Go by borrowing from Rust](https://getstream.io/blog/fixing-the-billion-dollar-mistake-in-go-by-borrowing-from-rust/)", June 14, 2018 - Nil pointer dereferences cause panics in production - it would be great if the type system would catch some of those.

## Typed nils
 
  - David Cheney, "[Typed nils in Go 2](https://dave.cheney.net/2017/08/09/typed-nils-in-go-2)", August 2017.

## Vendoring
  - Jeremy Loy, "[Go Modules and Vendoring](https://github.com/golang/go/issues/27227#issuecomment-420428896)", September 2018.