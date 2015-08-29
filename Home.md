Welcome to the Go wiki, a collection of information about the [Go Programming Language](https://golang.org/). [Awesome Go](http://awesome-go.com/) is another great resource for Go programmers, curated by the Go community.

Table of Contents
=================

+ [Getting started with Go](#getting-started-with-go)
+ [Working with Go](#working-with-go)
+ [Learning more about Go](#learning-more-about-go)
+ [The Go Community](#the-go-community)
+ [Using the go toolchain](#using-the-go-toolchain)
+ [Additional Go Programming Wikis](#additional-go-programming-wikis)
+ [Onlines Services that work with Go](#onlines-services-that-work-with-go)
+ [Troubleshooting Go Programs in Production](#troubleshooting-go-programs-in-production)
+ [Contributing to the Go Project](#contributing-to-the-go-project)
+ [Platform Specific Information](#platform-specific-information)
+ [Release Specific Information](#release-specific-information)


## Getting started with Go

  - [The Go Tour](http://tour.golang.org) is the best place to start.
  - [Effective Go](https://golang.org/doc/effective_go.html) will help you learn how to write idiomatic Go code.
  - [Go standard library documentation](https://golang.org/pkg/) to familiarize yourself with the standard library.
  - [Use the Go Playground](http://play.golang.org) to test out Go programs in your browser.
  - Still not convinced? Check out this list of [Go Users](GoUsers) and a few of their [Success tories](SuccessStories). We've also assembled a long list of reasons [why you should give Go a try](whygo).

##  Working with Go

Ready to write some Go code of your own? Here are a few links to help you  get started.

  - Install and Setup your Environment
    - Start here: [Official Installation Documentation](https://golang.org/doc/install)
    -  If you prefer to install from source, [read this first](https://golang.org/doc/install/source). 
      - [InstallFromSource](InstallFromSource) - Additional tips on source installs.
    - Having installation problems? [InstallTroubleShooting](InstallTroubleShooting)
    - Make sure you have your [$GOPATH environment variable set correctly](https://golang.org/doc/install/source#gopath)
      - If you need additional tips on using [$GOPATH, go here](GOPATH).
    - [MultipleGoRoots](MultipleGoRoots) - More advanced information on working with multiple go installations and the `$GOROOT` variable.
  - [Go IDEs and Editors](IDEsAndTextEditorPlugins) - Information on how to use your favorite editor with Go.
  - Finding Go Libraries & Tools
    - Start by searching [godoc.org](http://godoc.org)
    - Then check this list of [Go open source projects](Projects) for additional search tools and curated lists.
  - [Managing your dependencies](PackageManagementTools) - An overview of the tools you can use to manage the libraries that your appliction depends on.
  - Publishing Go Packages as Open Source
    - Getting ready to publish your package? [Start here.](PackagePublishing)
    - [The Go Checklist](https://github.com/matttproud/gochecklist) - A comprehensive guide for publishing a project.
    - [How to layout your GitHub repo](GithubCodeLayout) to make it easy to for other Go programmers to use with the `go get` command.
    - [Go Package, Go](https://johnsto.co.uk/blog/go-package-go) - A few recommendations for making Go packages easy to use.

## Learning more about Go

Once you have an overview of the language, here are resources you can use to learn more about the language.

  - [Learning Go](Learn) - A collection of resources for learning Go - beginner to advanced.
    - [The Go Bridge Foundry](https://github.com/gobridge) - A member of the [Bridge Foundry](http://bridgefoundry.org/) family, offering a complete set of free Go training materials with the goal of bringing Go to underrepresented communities.
    - [More on concurrency](LearnConcurrency)
    - [More on error handling](LearnErrorHandling)
    - [More on server programming](LearnServerProgramming)
    - [More on testing](LearnTesting)
  - [Books](Books) - A list of Go books that have been published (ebook, paper)
  - Videos, Talks and Presentations
    - [GopherVids](http://gophervids.appspot.com/) is a searchable index of videos about Go.
    - [GoTalks](GoTalks) - A collection of talks from Go conferences and meetups.
    - [Screencasts](Screencasts)
  - [Articles](Articles) - A collection of articles to help you learn more about Go.
  - [Training](Training) - Free and commercial, online and classroom training for Go.
  - [Universtiry Courses](Courses) - A list of CS programs and classes using Go.    
  - [Resources for non-English speakers](NonEnglish)

## The Go Community

Here are some of the places where you can find Gophers online. To get a sense of what it means to be a member of the Go community, read [Damian Gryski's keynote from the GolankUK 2015 conference](https://medium.com/@dgryski/the-go-community-f0d00e3a19e) or watch [Andrew Gerrand's closing keynote from GopherCon 2015](https://www.youtube.com/watch?v=0ht89TxZZnk).

- Mailing Lists
  - The mailing list for Go users is [golang-nuts](https://groups.google.com/forum/#!forum/golang-nuts) - very high traffic.
    - Before you post, [check to see if it's already been answered](http://stackoverflow.com/tags/go), then read [these tips on how to ask a good question](HowToAsk)
  - For discussios about the core Go open source project, join [golang-dev](https://groups.google.com/forum/#!forum/golang-dev).
  - To get just our release announcements, join [golang-announce](https://groups.google.com/forum/#!forum/golang-announce)
- Chat, discussion and other forums
  - We have a [Gophers Slack Channel](http://gophers.slack.com/). Requires you to [request membership here](http://blog.gopheracademy.com/gophers-slack-community/)
  - For IRC fans there is #go-nuts on irc.freenode.net which is [indexed here](https://botbot.me/freenode/go-nuts/).
  - There is also a [/r/golang](http://reddit.com/r/golang) sub-reddit.
  - On Twitter, follow the [@golang](https://twitter.com/golang) account and keep tabs on the [#golang](https://twitter.com/search?q=%23golang&src=typd) hashtag.
  - We've also got a landing page on [Stack Overvflow](http://stackoverflow.com/tags/go) for Go Q&A.
- User Groups & Meetups - There are [Go Meetups in many cities](http://www.meetup.com/find/?allMeetups=false&keywords=golang&radius=Infinity&userFreeform=Sunnyvale%2C+CA&mcId=z94086&mcName=Sunnyvale%2C+CA&sort=recommended&eventFilter=mysugg)
    - See here for [additional information GoUserGroups](GoUserGroups)
- [Conferences](Conferences) - A list of upcoming and past Go conferences and major events.
- A comprehensive list of companies using Go: [Go Users](GoUsers)
- Learn more about the [Go Gohper images](Gopher) by Renee French.

## Using the go toolchain

  - Start with the standard documentation for the `go` command [available here](https://golang.org/cmd/go/)
  - Using the Go 1.5 `GO15VENDOREXPERIMENT`
    - Start here for the [official documentation](https://golang.org/cmd/go/#hdr-Vendor_Directories).
    - [Overview with examples](http://icanhazdowntime.org/post/2015-07-09-go-vendor-experiment/) by [@freeformz](https://twitter.com/freeformz).
    - See also [PackageManagementTools](PackageManagementTools) for additional details.
  - Shared libraries and Go (buildmode)
    - [Go Shared Libraries](https://github.com/jbuberel/buildmodeshared) - Examples for creating and using shared libraries from Go and Python.
    - [gohttplib](https://github.com/shazow/gohttplib) - An experiment in using Go 1.5 buildmode=c-shared.
    - [Sharing Golang Packages to C](http://blog.ralch.com/tutorial/golang-sharing-libraries/) - A tutorial by [@ralch](https://twitter.com/ralch).
    - [Calling Go libraries from Python](https://blog.filippo.io/building-python-modules-with-go-1-5/) - by Filippo Valsorda
    - [Calling Go libraries from Ruby](http://c7.se/go-and-ruby-ffi/) - by Peter Hellberg
  - See the wikis below for additional details:
    - [GoGetTools](GoGetTools)
    - [GoGetProxyConfig](GoGetProxyConfig)
    - [cgo](cgo)
    - [CompilerOptimizations](CompilerOptimizations)
    - [GccgoCrossCompilation](GccgoCrossCompilation)
    - [GcToolchainTricks](GcToolchainTricks)
    - [GoGenerateTools](GoGenerateTools)

## Additional Go Programming Wikis

  - [Why Go doesn't Support Generics: A Summary of Go Generics Discussions](https://docs.google.com/document/d/1vrAy9gMpMoS3uaVphB32uVXX4pi-HnNjkMEgyAHX4N4/preview) - Start here before you join the debate.
  - Concurrency
    - [Timeouts](Timeouts) - Abandon async calls that take too long
    - [LockOSThread](LockOSThread)
    - [MutexOrChannel](MutexOrChannel) - When to use one vs the other
    - [RaceDetector](RaceDetector) - How to detect and fix race conditions
  - Working with Databases
    - [database/sql](http://go-database-sql.org/) - Online tutorial for working with the database/sql package.
    - [SQLDrivers](SQLDrivers)
    - [SQLInterface](SQLInterface)
  - From other languages
    - [Go for Java Programmers](https://www.nada.kth.se/~snilsson/go_for_java_programmers/)
    - [Go for C++ Programmers](GoForCPPProgrammers)
  - [Comments](Comments)
  - [CommonMistakes](CommonMistakes)
  - [Errors](Errors)
  - [GcToolchainTricks](GcToolchainTricks)
  - [GoStrings](GoStrings)
  - [Hashing](Hashing)
  - [HttpFetch](HttpFetch)
  - [HttpStaticFiles](HttpStaticFiles)
  - [InterfaceSlice](InterfaceSlice)
  - [Iota](Iota)
  - [MethodSets](MethodSets)
  - [PanicAndRecover](PanicAndRecover)
  - [Range](Range)
  - [RateLimiting](RateLimiting)
  - [Rationales](Rationales)
  - [SendingMail](SendingMail)
  - [SignalHandling](SignalHandling)
  - [SimultaneousAssignment](SimultaneousAssignment)
  - [SliceTricks](SliceTricks)
  - [Switch](Switch)
  - [TableDrivenTests](TableDrivenTests)
  

## Onlines Services that work with Go

If you're looking for services that support Go, here's a list to get you started.

  - Cloud Computing - Go is well supported on most cloud service providers.
    - [Amazone Web Services](https://github.com/aws/aws-sdk-go)
    - [Azure](https://github.com/Azure/azure-sdk-for-go)
    - [Digital Ocean](https://github.com/digitalocean/godo)
    - [Google Cloud Platform and App Engine for Go](https://cloud.google.com/appengine/docs/go/)
    - [Heroku](https://github.com/heroku/heroku-buildpack-go)
    - See here for [information on additional providers](ProviderIntegration)
  - [Continuous Integration and Continuous Deployment](HostedContinuousIntegration) - Go is well supported by most CI/CD framworks
  - Monitoring/Logging
    - [DeferPanic](http://deferpanic.com) - Dedicated Go application performance monitoring.
  - Package and Dependency Management
    - [Gopkg.in](http://labix.org/gopkg.in) is a source for stable Go libraries, provided by Gustavo Niemeyer.
    - [Stable Lib](https://stablelib.com/) is a service that provides stable Go packages with long-term support.

## Troubleshooting Go Programs in Production

  - Understand the performance of you Go apps using the [pprof package](http://blog.golang.org/profiling-go-programs)
  - Heap Dumps
    - [heapdump13](heapdump13)
    - [heapdump14](heapdump14)

## Contributing to the Go Project

  - Start by reading the [Go Contribution Guidelines](https://golang.org/doc/contribute.html)
  - If you'd like to propose a change to the Go project, start by reading the [Go Change Proposal Process](https://github.com/golang/proposal)
    -  An archive of [design documents is also available](DesignDocuments)
  - Go releases happen on ~6 month intervals. [See here for more information](Go-Release-Cycle)
  - Want to know more about how the [Go source sub-repositories are structured?](SubRepositories)
  - The Go project requires that all code be reviewed before it is submitted. 
    - Read more about our [code review practices](CodeReview)
    - If you're commenting on code under review, please read [these guidelines](CodeReviewComments)
  - Issues
    - Bug reports and feature requests should be filed using the [Github issue tracker](https://github.com/golang/go/issues)
    - Want to understand how we [handle issues that are reported?](HandlingIssues)
  - Project Dashboards
    - [Go Builds Dashboard info](DashboardBuilders)
    - [Performance Dashboard info](PerfDashboard)

## Platform Specific Information

  - Considering porting Go to a new platform? [Read our porting policy first](PortingPolicy)
  - [Mobile](Mobile)
  - [Ubuntu](Ubuntu)
  - Windows
    - [WindowsBuild](WindowsBuild)
    - [WindowsCrossCompiling](WindowsCrossCompiling)
    - [WindowsDLLs](WindowsDLLs)
    - [WindowsSupport](WindowsSupport)
  - [GoArm](GoArm)
  - [ChromeOS](ChromeOS)
  - [NetBSD](NetBSD)
  - [OpenBSD](OpenBSD)
  - [FreeBSD](FreeBSD)
  - [NativeClient](NativeClient)

## Release Specific Information

  - [Go1point1Gotchas](Go1point1Gotchas)
  - [OlderVersions](OlderVersions)

Notes:

- Please refrain from changing the title of the wiki pages, as some of them might be linked to from [golang.org](https://golang.org) or other websites.