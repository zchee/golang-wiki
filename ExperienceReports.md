# Experience Reports

This page collects experience reports about problems with Go that might inform our design of solutions to those problems.

__The best experience reports tell: what we wanted to do, what we actually did, why that wasn’t great,
illustrated by real, concrete examples, ideally from production use.__ Please write these reports about the problems most significant to you, post them on your own blog or on Medium, and then link them here.

If you do not have permission to edit the wiki to add an article to this list, [please file an issue](https://golang.org/issue/new).

Please keep the overall page themselves sorted alphabetically by section (Error Handling before Logging, and so on).
Within a section, please keep articles sorted chronologically.
It's helpful to include a one-phrase summary of the point of each article.

Add new sections as appropriate.

## Context

  - Sam Vilain, “[Using Go's context library for making your logs make sense](https://blog.gopheracademy.com/advent-2016/context-logging/),” December 2016, about extracting structured log values from context.
  - Jon Calhoun, “[Pitfalls of context values and how to avoid or mitigate them in Go](https://www.calhoun.io/pitfalls-of-context-values-and-how-to-avoid-or-mitigate-them/),” February 2017.

## Diagnostics and Debugging

  - Entries here.

## Error Handling

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

## Generics

  - Bouke van der Bijl, “[Idiomatic Generics in Go](https://web.archive.org/web/20141001043016/http://bouk.co/blog/idiomatic-generics-in-go/),” September 2014.
  - Craig Weber, “[Living without generics in Go](https://web.archive.org/web/20141227092139/http://www.weberc2.com/posts/2014/12/12/living-without-generics.txt),” December 2014.
  - Shashank Sharma, “[Poor man's generics in Golang (Go)](https://codeblog.shank.in/poor-mans-generics-in-golang/),” May 2016.
  - Niek Sanders, “[Overhead of Go's generic sort](https://github.com/nieksand/sortgenerics),” September 2016,
    documenting the overhead of sorting using sort.Interface instead of specialized code.
  - Jon Calhoun, “[Using code generation to survive without generics in Go](https://dev.to/joncalhoun/using-code-generation-to-survive-without-generics-in-go),” May 2017.
  - Jon Bodner, “[Closures are the Generics for Go](https://medium.com/capital-one-developers/closures-are-the-generics-for-go-cb32021fb5b5),” June 2017.

## Large-Scale Software Development
  - Russ Cox, “[Codebase Refactoring (with help from Go)](https://talks.golang.org/2016/refactor.article),” November 2016, laying out the case for type aliases.

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

## Performance

  - Entries here.

## Time 

  - John Graham-Cumming, “[How and Why the Leap Second Affected Cloudflare DNS](https://blog.cloudflare.com/how-and-why-the-leap-second-affected-cloudflare-dns/),” January 2017, about timing across leap seconds.