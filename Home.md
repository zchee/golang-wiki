Welcome to the Go wiki, a collection of information about the [Go Programming Language](https://golang.org/).

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
  - Still not convinced? Check out this list of [Go Users](GoUsers.md) and a few of their [Success tories](SuccessStories.md). We've also assembled a long list of reasons [why you should give Go a try](whygo.md).

##  Working with Go

Ready to write some Go code of your own? Here are a few links to help you  get started.

  - Install and Setup your Environment
    - Start here: [Official Installation Documentation](https://golang.org/doc/install)
    -  If you prefer to install from source, [read this first](https://golang.org/doc/install/source). 
      - [InstallFromSource](InstallFromSource.md) - Additional tips on source installs.
    - Having installation problems? [InstallTroubleShooting](InstallTroubleShooting.md)
    - Make sure you have your [$GOPATH environment variable set correctly](https://golang.org/doc/install/source#gopath)
      - If you need additional tips on using [$GOPATH, go here](GOPATH.md).
    - [MultipleGoRoots](MultipleGoRoots.md) - More advanced information on working with multiple go installations and the `$GOROOT` variable.
  - [Go IDEs and Editors](IDEsAndTextEditorPlugins.md) - Information on how to use your favorite editor with Go.
  - Finding Go Libraries & Tools
    - Start by searching [godoc.org](http://godoc.org)
    - Then check this list of [Go open source projects](Projects.md) for additional search tools and curated lists.
  - [Managing your dependencies](PackageManagementTools.md) - An overview of the tools you can use to manage the libraries that your appliction depends on.
  - Publishing Go Packages as Open Source
    - Getting ready to publish your package? [Start here.](PackagePublishing.md)
    - [How to layout your GitHub repo](GithubCodeLayout.md) to make it easy to for other Go programmers to use with the `go get` command.

## Learning more about Go

Once you have an overview of the language, here are resources you can use to learn more about the language.

  - [Books](Books.md) - A list of Go books that have been published (ebook, paper)
  - [Articles](Articles.md) - A collection of articles to help you learn more about Go.
  - Classes and Training
    - [Courses](Courses.md) - Online classes you can take (free & paid) to learn more about Go.
    - [Learn](Learn.md) - Additional resources and tutorials.
      - [LearnConcurrency](LearnConcurrency.md)
      - [LearnErrorHandling](LearnErrorHandling.md)
      - [LearnServerProgramming](LearnServerProgramming.md)
      - [LearnTesting](LearnTesting.md)
  - Videos, Talks and Presentations
    - [GoTalks](GoTalks.md) - A collection of talks from Go conferences and meetups.
    - [Screencasts](Screencasts.md)
  - [Resources for non-English speakers](NonEnglish.md)

## The Go Community

Here are some of the places where you can find Gophers online

- Mailing Lists
  - The mailing list for Go users is [golang-nuts](https://groups.google.com/forum/#!forum/golang-nuts) - very high traffic.
    - Before you post, [check to see if it's already been answered](http://stackoverflow.com/tags/go), then read [these tips on how to ask a good question](HowToAsk.md)
  - For discussios about the core Go open source project, join [golang-dev](https://groups.google.com/forum/#!forum/golang-dev).
  - To get just our release announcements, join [golang-announce](https://groups.google.com/forum/#!forum/golang-announce)
- Chat, discussion and other forums
  - We have a [Gophers Slack Channel](http://gophers.slack.com/). Requires you to [request membership here](http://blog.gopheracademy.com/gophers-slack-community/)
  - For IRC fans there is #go-nuts on irc.freenode.net which is [indexed here](https://botbot.me/freenode/go-nuts/).
  - There is also a [/r/golang](http://reddit.com/r/golang) sub-reddit.
  - On Twitter, follow the [@golang](https://twitter.com/golang) account and keep tabs on the [#golang](https://twitter.com/search?q=%23golang&src=typd) hashtag.
  - We've also got a landing page on [Stack Overvflow](http://stackoverflow.com/tags/go) for Go Q&A.
- User Groups & Meetups - There are [Go Meetups in many cities](http://www.meetup.com/find/?allMeetups=false&keywords=golang&radius=Infinity&userFreeform=Sunnyvale%2C+CA&mcId=z94086&mcName=Sunnyvale%2C+CA&sort=recommended&eventFilter=mysugg)
    - See here for [additional information GoUserGroups](GoUserGroups.md)
- Conferences
- Looking for companies that are using Go?

  - Go Gopher Images
    - [Gopher](Gopher.md)


## Using the go toolchain

  - Start with the standard documentation for the `go` command [available here](https://golang.org/cmd/go/)
  - See the wikis below for additional details:
    - [GoGetTools](GoGetTools.md)
    - [GoGetProxyConfig](GoGetProxyConfig.md)
    - [cgo](cgo.md)
    - [CompilerOptimizations](CompilerOptimizations.md)
    - [GccgoCrossCompilation](GccgoCrossCompilation.md)
    - [GcToolchainTricks](GcToolchainTricks.md)
    - [GoGenerateTools](GoGenerateTools.md)

## Additional Go Programming Wikis
  - Working with Databases
    - [SQLDrivers](SQLDrivers.md)
    - [SQLInterface](SQLInterface.md)
  - [Comments](Comments.md)
  - [CommonMistakes](CommonMistakes.md)
  - [Errors](Errors.md)
  - [GcToolchainTricks](GcToolchainTricks.md)
  - [GoForCPPProgrammers](GoForCPPProgrammers.md)
  - [GoStrings](GoStrings.md)
  - [GoVsGenerics](GoVsGenerics.md)
  - [Hashing](Hashing.md)
  - [HttpFetch](HttpFetch.md)
  - [HttpStaticFiles](HttpStaticFiles.md)
  - [InterfaceSlice](InterfaceSlice.md)
  - [Iota](Iota.md)
  - [LockOSThread](LockOSThread.md)
  - [MethodSets](MethodSets.md)
  - [MutexOrChannel](MutexOrChannel.md)
  - [PanicAndRecover](PanicAndRecover.md)
  - [RaceDetector](RaceDetector.md)
  - [Range](Range.md)
  - [RateLimiting](RateLimiting.md)
  - [Rationales](Rationales.md)
  - [SendingMail](SendingMail.md)
  - [SignalHandling](SignalHandling.md)
  - [SimultaneousAssignment](SimultaneousAssignment.md)
  - [SliceTricks](SliceTricks.md)
  - [Switch](Switch.md)
  - [TableDrivenTests](TableDrivenTests.md)
  - [Timeouts](Timeouts.md)

## Onlines Services that work with Go

If you're looking for services that support Go, here's a list to get you started.

  - Cloud Computing - Go is well supported on most cloud service providers.
    - [Amazone Web Services](https://github.com/aws/aws-sdk-go)
    - [Azure](https://github.com/Azure/azure-sdk-for-go)
    - [Digital Ocean](https://github.com/digitalocean/godo)
    - [Google Cloud Platform and App Engine for Go](https://cloud.google.com/appengine/docs/go/)
    - [Heroku](https://github.com/heroku/heroku-buildpack-go)
    - See here for [information on additional providers](ProviderIntegration.md)
  - Continuous Integration and Continuous Deployment - Go is well supported by all CI/CD framworks
    - [Jenkins](https://wiki.jenkins-ci.org/display/JENKINS/Go+Plugin)
    - [Travis](http://docs.travis-ci.com/user/languages/go/)
    - [Werker](http://devcenter.wercker.com/quickstarts/building/golang.html)
    - More information [is available here](HostedContinuousIntegration.md)
  - Monitoring/Logging
    - [DeferPanic](http://deferpanic.com) - Dedicated Go application performance monitoring.
  - Package and Dependency Management
    - [Gopkg.in](http://labix.org/gopkg.in) is a source for stable Go libraries, provided by Gustavo Niemeyer.

## Troubleshooting Go Programs in Production

  - Understand the performance of you Go apps using the [pprof package](http://blog.golang.org/profiling-go-programs)
  - Heap Dumps
    - [heapdump13](heapdump13.md)
    - [heapdump14](heapdump14.md)

## Contributing to the Go Project

  - Start by reading the [Go Contribution Guidelines](https://golang.org/doc/contribute.html)
  - If you'd like to propose a change to the Go project, start by reading the [Go Change Proposal Process](https://github.com/golang/proposal)
    -  An archive of [design documents is also available](DesignDocuments.md)
  - Go releases happen on ~6 month intervals. [See here for more information](Go-Release-Cycle.md)
  - Want to know more about how the [Go source sub-repositories are structured?](SubRepositories.md)
  - The Go project requires that all code be reviewed before it is submitted. 
    - Read more about our [code review practices](CodeReview.md)
    - If you're commenting on code under review, please read [these guidelines](CodeReviewComments.md)
  - Issues
    - Bug reports and feature requests should be filed using the [Github issue tracker](https://github.com/golang/go/issues)
    - Want to understand how we [handle issues that are reported?](HandlingIssues.md)
  - Project Dashboards
    - [Go Builds Dashboard info](DashboardBuilders.md)
    - [Performance Dashboard info](PerfDashboard.md)

## Platform Specific Information

  - Considering porting Go to a new platform? [Read our porting policy first](PortingPolicy.md)
  - [Mobile](Mobile.md)
  - [Ubuntu](Ubuntu.md)
  - Windows
    - [WindowsBuild](WindowsBuild.md)
    - [WindowsCrossCompiling](WindowsCrossCompiling.md)
    - [WindowsDLLs](WindowsDLLs.md)
    - [WindowsSupport](WindowsSupport.md)
  - [GoArm](GoArm.md)
  - [ChromeOS](ChromeOS.md)
  - [NetBSD](NetBSD.md)
  - [OpenBSD](OpenBSD.md)
  - [FreeBSD](FreeBSD.md)
  - [NativeClient](NativeClient.md)

## Release Specific Information

  - [Go1point1Gotchas](Go1point1Gotchas.md)
  - [OlderVersions](OlderVersions.md)

Notes:

- Please refrain from changing the title of the wiki pages, as some of them might be linked to from [golang.org](https://golang.org) or other websites.