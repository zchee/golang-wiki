
Please keep all entries in reverse chronological order (most recent first)

Table of Contents
=================

* [Indexes](#article-indexes)
* [General](#general)
* [Concurrency / Channels](#concurrency--channels)
* [Containers & Docker](#containers--docker)
* [Cross Platform Development](#cross-platform-development)
* [Error Handling](#error-handling)
* [Interfaces / OOP](#interfaces--oop)
* [Mobile Applications](#mobile-applications)
* [Modules](#modules)
* [Performance and Profiling](#performance-and-profiling)
* [Pointers/References/Memory](#pointers-references-and-memory-management)
* [Reflection](#reflection)
* [Security](#security)
* [Testing](#testing)
* [Web & API Development](#web--api-development)
* [Misc](#misc)
* [Chinese](#chinese)
* [Czech](#czech)
* [German](#german)
* [Japanese](#japanese)
* [Korean](#korean)

## Article Indexes

  * [Collection of #golang posts on Medium](https://medium.com/tag/golang) _latest_
  * [Go articles from Dr. Dobbs](http://www.drdobbs.com/sitesearch?sort=publishDate+desc&queryText=golang&type=site) _latest_
  * [Slideshare Collection of #golang presentations](http://www.slideshare.net/search/slideshow?searchfrom=header&q=golang&ud=any&ft=all&lang=**&sort=) _latest_
  * [Short Go tutorials on SocketLoop](https://www.socketloop.com/tagsearch/golang) _latest_
  * [An Introduction to Go](https://tutorialedge.net/course/golang/) _latest_

## General
  * [Go Defer Simplified with Practical Visuals](https://blog.learngoprogramming.com/golang-defer-simplified-77d3b2b817ff) _2017-11-23_
  * [The Zoo of Go Funcs](https://blog.learngoprogramming.com/go-functions-overview-anonymous-closures-higher-order-deferred-concurrent-6799008dde7b) _2017-11-09_
  * [Ultimate Guide to Go Variadic Functions](https://blog.learngoprogramming.com/golang-variadic-funcs-how-to-patterns-369408f19085) _2017-11-02_
  * [Go Funcs-Baby Gopher's Visual Guide](https://blog.learngoprogramming.com/golang-funcs-params-named-result-values-types-pass-by-value-67f4374d9c0a) _2017-10-27_
  * [Ultimate Visual Guide to Go Enums](https://blog.learngoprogramming.com/golang-const-type-enums-iota-bc4befd096d3) _2017-10-19_
  * [Learn Go Constants](https://blog.learngoprogramming.com/learn-golang-typed-untyped-constants-70b4df443b61) _2017-10-10_
  * [Learn Go Variables](https://blog.learngoprogramming.com/learn-go-lang-variables-visual-tutorial-and-ebook-9a061d29babe) _2017-10-04_
  * [Introduction to Go Packages](https://blog.learngoprogramming.com/definitive-guide-to-go-packages-focus-on-the-fundamentals-to-empower-your-skills-d14aae7cd321) _2017-09-26_
  * [About Go Language — An Overview](https://blog.learngoprogramming.com/about-go-language-an-overview-f0bee143597c) _2017-09-20_
  * [Debugging code generation in Go](https://rakyll.org/codegen/) _2016-10-15_
  * [Go tooling essentials](https://rakyll.org/go-tool-flags/) _2016-09-25_
  * [Go from PHP engineer's perspective](http://sobit.me/2016/02/25/go-from-php-engineers-perspective/) _2016-02-25_
  * [Go Proverbs, Illustrated](http://www.gregosuri.com/2015/12/04/go-proverbs-illustrated/) _2015-12-04_
  * [A whirlwind tour of Go’s runtime environment variables](http://dave.cheney.net/2015/11/29/a-whirlwind-tour-of-gos-runtime-environment-variables) _2015-11-29_
  * [Idiomatic Doc Comments: Document your function, not your function signature](http://whipperstacker.com/2015/10/14/idiomatic-doc-comments-document-your-function-not-your-function-signature/) _2015-10_14_
  * [Best Practices for a new Go Developer](https://medium.com/@IndianGuru/best-practices-for-a-new-go-developer-8660384302fc) _2015-09-01_
  * [Golang Refactoring Tools](http://blog.ralch.com/tutorial/golang-tools-refactoring/) _2015-08-30_
  * [Working with Files in Go](http://www.devdungeon.com/content/working-files-go) _2015-08-23_
  * [Defer Fun](https://blog.klauspost.com/defer-fun/) _2015-07-25_
  * [Things I learned teaching Go - Francesc Campoy](https://medium.com/@francesc/dotgo-things-i-learned-teaching-go-e999f33298cf) _2014-11-24_  
  * [Understanding Go Packages](http://thenewstack.io/understanding-golang-packages/) _2014-11-01_
  * [Structuring Applications in Go](https://medium.com/@benbjohnson/structuring-applications-in-go-3b04be4ff091#.kj6eym1u4) _2014-06-06_
  * [Functional Options for Friendly APIs](http://dave.cheney.net/2014/10/17/functional-options-for-friendly-apis) _2014-10-17_
  * [Go Programming for Beginners](http://thenewstack.io/the-new-stack-intros-go-programming-for-beginners/) _2014-10-01_
  * [Switching from Python to Go](https://www.spacemonkey.com/blog/posts/go-space-monkey) _2014-04-21_
  * [Google Go: The Good, the Bad, and the Meh](http://blog.carlsensei.com/post/42828735125) _2013-02-10_
  * [What I Love About Go](http://npf.io/2013/01/what-i-love-about-go) _2013-01-25_
  * [Why I program in Go](http://tech.t9i.in/2013/01/why-program-in-go/) _2013-01-05_
  * [Go: A New Language for a New Year](http://kylelemons.net/2012/01/go-new-language-new-year/) _2012-01-06_
  * [Why you PHP guys should learn Golang](http://www.mikespook.com/2012/08/why-you-php-guys-should-learn-golang/) _2012-08-10_
  * [Why I went from Python to Go (and not node.js)](http://jordanorelli.tumblr.com/post/31533769172/why-i-went-from-python-to-go-and-not-node-js) _2012-09-14_

## Concurrency / Channels

  * [Learning Go concurrency through illustrations](https://medium.com/@trevor4e/learning-gos-concurrency-through-illustrations-8c4aff603b3) _2018-06-21_
  * [Using contexts to avoid leaking goroutines](https://rakyll.org/leakingctx/) _2016-10-25_
  * [Concurrency in Go](http://www.minaandrawos.com/2015/12/06/concurrency-in-golang/) _2015-12-06_
  * [Very basic concurrency for beginners in Go](https://medium.com/@matryer/very-basic-concurrency-for-beginners-in-go-663e63c6ba07#.n831uhdiq) _2015-11-18_
  * [Exploting Powerful Cloud Services with Go](https://medium.com/@sathishvj/exploiting-your-powerful-cloud-servers-with-go-lang-s-concurrency-eae5f4c7526) _2015-10-11_
  * [3 Trivial Concurrency Exercises for the Confused Newbie Gopher](http://whipperstacker.com/2015/10/05/3-trivial-concurrency-exercises-for-the-confused-newbie-gopher/) _2015-10-05_
  * [Golang lock-free values with atomic.Value](https://texlution.com/post/golang-lock-free-values-with-atomic-value/) _2015-08-21_
  * [Golang Pearl: Thread-safe writes and double checked locking in Go](http://blog.launchdarkly.com/golang-pearl-thread-safe-writes-and-double-checked-locking-in-go/) _2015-07-21_
  * [Building a Telnet Server in Go](http://synflood.at/tmp/golang-slides/mrmcd2012.html) _2015-08-28_
  * [Fundamentals of concurrent programming](http://www.nada.kth.se/~snilsson/concurrency/) _2013-01-27_
  * [Golang: Funny Play with Channel](http://www.mikespook.com/2012/05/golang-funny-play-with-channel/) _2012-05-25_
  * [Unlimited Buffering with Low Overhead](http://rogpeppe.wordpress.com/2010/02/10/unlimited-buffering-with-low-overhead/) _2010-02-10_
  * [Concurrent Idioms #1: Broadcasting values in Go with linked channels](http://rogpeppe.wordpress.com/2009/12/01/concurrent-idioms-1-broadcasting-values-in-go-with-linked-channels/) _2009-12-01_

## Containers & Docker

  * [Deploying a Go app to a minimal Docker container](http://www.giantflyingsaucer.com/blog/?p=5720) _2015-10-01_
  * [Fetching a remote configuration using Docker and Consul](http://www.giantflyingsaucer.com/blog/?p=5701) _2015-09-30_
  * [Joining the Docker Ship and Go](http://thenewstack.io/make-a-restful-json-api-go/) _2015-07-01_
  * [Building Minimal Docker Images for Go](http://blog.codeship.com/building-minimal-docker-containers-for-go-applications/) _2015-04-23_

## Cross-Platform Development
  * [Releasing cross-platform Go binaries using Goxc and BinTray in 5 minutes](http://jbu.io/2015/11/29/releasing-cross-platform-go-binaries-using-goxc-and-bintray-in-5-minutes/) _2015-11-29_
  * [Calling Go from Swift](https://rakyll.org/swift/) _2015-10-3_
  * [On Go, portability, and system interfaces](http://garrett.damore.org/2015/09/on-go-portability-and-system-interfaces.html) _2015-09-22_
  * [Go cross compilation](https://rakyll.org/cross-compilation/) _2015-09-8_

## Error Handling

  * [Returning Errors](https://npf.io/2015/10/errors/) _2015-10-10_
  * [Inspecting Errors](http://dave.cheney.net/2014/12/24/inspecting-errors) _2014-12-24_

## Interfaces / OOP

  * [Generics in Golang with Code Generation](http://blog.ralch.com/tutorial/golang-code-generation-and-generics/) _2015-10-18_
  * [Composition with Go](http://www.goinggo.net/2015/09/composition-with-go.html) _2015-09-13_
  * [Sorting Inventory Items in Go - the sort.Interface](https://adampresley.github.io/2015/09/06/sorting-inventory-items-in-go.html) _2015-09-06_
  * [Loose Coupling in Go Lang](https://blog.8thlight.com/javier-saldana/2015/02/06/loose-coupling-in-go-lang.html) _2015-02-06_
  * [Interface Types in Go](https://medium.com/@rakyll/interface-pollution-in-go-7d58bccec275) _2014-10-18_
  * [How to use interfaces in Go](http://jordanorelli.tumblr.com/post/32665860244/how-to-use-interfaces-in-go) _2012-10-01_
  * [Go Object Oriented Design](http://nathany.com/good) _2013-01-14_
  * [It is ridiculously easy to refactor Go](http://www.onebigfluke.com/2013/01/it-is-ridiculously-easy-to-refactor-go.html) _2013-01-27_
  * [Functional Iteration in Go](http://hackthology.com/functional-iteration-in-go.html) _2013-12-13_
  * [Interfaces in Go - Russ Cox](http://research.swtch.com/interfaces) _2009-12-01_


## Mobile Applications

Start by reading the [overview of mobile development](Mobile) documentation first.

  * [Go Mobile: Next generation of mobile apps](https://www.linkedin.com/pulse/go-mobile-next-generation-apps-daniele-baroncelli) _2015-09-18_
  * [iOS Apps with Go - Video by Josh Deprez](https://www.youtube.com/watch?v=bftMhhMIJNo) _2015-09-17_
  * [5 Part Series - Mobile Go](https://medium.com/using-go-in-mobile-apps)

## Modules

  * [Introduction to Go Modules](https://roberto.selbach.ca/intro-to-go-modules/) _2018-08-18_

## Performance and Profiling
  * [Mutex profile](https://rakyll.org/mutexprofile/) _2016-12-19_
  * [How to Optimize Garbage Collection in Go](http://www.cockroachlabs.com/blog/how-to-optimize-garbage-collection-in-go/) _2015-11-23_
  * [Golang Escape Analysis](http://www.agardner.me/golang/garbage/collection/gc/escape/analysis/2015/10/18/go-escape-analysis.html) _2015-10-18_
  * [A Pattern for Optimizing Go](http://blog.signalfx.com/a-pattern-for-optimizing-go) _2015-09-24_
  * [Golang Performance Tips](https://joshrendek.com/2015/09/golang-performance-tips/) _2015-09-20_
  * [Answering your own (performance) questions in Go](http://www.sanarias.com/blog/915LearningtoansweryourownquestionsinGo) _2015-09-15_
  * [Concise Guide to profiling go programs](https://medium.com/@tjholowaychuk/profiling-golang-851db2d9ae24) _2014-08-09_
  * [Go Performance Observations](http://hashrocket.com/blog/posts/go-performance-observations) _2014-08-07_
  * [Debugging performance issues in Go programs - Intel](https://software.intel.com/en-us/blogs/2014/05/10/debugging-performance-issues-in-go-programs) _2014-05-10_
  * [How to write benchmarks in Go](http://dave.cheney.net/2013/06/30/how-to-write-benchmarks-in-go) _2013-06-30_
  * [Profiling Go Programs - Go blog](http://blog.golang.org/profiling-go-programs) _2011-06-24_

## Pointers, References and Memory Management

  * [Equality and Type Aliases](https://akutz.wordpress.com/2015/09/02/golang-equality-and-type-aliases/) _2015-09-02_
  * [Pointers vs References](http://spf13.com/post/go-pointers-vs-references/) _2014-06-01_
  * [Recycling Memory Buffers in Go](https://blog.cloudflare.com/recycling-memory-buffers-in-go/) _2013-08-24_
  * [Learning Go Types](http://www.laktek.com/2012/01/27/learning-go-types/) _2012-01-27_

## Reflection

  * [Go Reflection Index](https://jimmyfrasche.github.io/go-reflection-codex/) by Jimmy Frasche

## Security

  * [Mutual TLS authentication in Go](http://www.levigross.com/2015/11/21/mutual-tls-authentication-in-go/) _2015-11-21_
  * [Whispered Secrets - The case for building software with privacy as a primary concern](http://www.slideshare.net/feyeleanor/whispered-secrets-52966860) _2015-09-19_

## Testing

  * [Getting Started with BDD in Go Using Ginkgo](https://semaphoreci.com/community/tutorials/getting-started-with-bdd-in-go-using-ginkgo) _2016-07-12_
  * [Integration testing in Go using Docker](https://divan.github.io/posts/integration_testing/) _2015-12-07_
  * [Debugging Go Programs with Delve](https://blog.gopheracademy.com/advent-2015/debugging-with-delve/) _2015-12-03_
  * [Upgrade Your Appengine Tests with Testify](http://csfortheslothful.blogspot.com/2015/11/upgrade-your-appengine-tests-with.html) _2015_11_21_

## Web & API Development

Start by reading the [overview of server programming](LearnServerProgramming) documentation first.
  * [Get started with Go and WebAssembly](https://medium.com/@sendilkumarn/getting-started-into-go-and-webassembly-8491b133a616) _2018-08-14_
  * [HTTP/2 Server Push](https://rakyll.org/http2push/) _2016-12-10_
  * [Preventing Cross-Site Request Forgery in Go](https://elithrar.github.io/article/preventing-csrf-attacks-in-go/) _2015-12-14_
  * [goa: Untangling Microservices](https://blog.gopheracademy.com/advent-2015/goaUntanglingMicroservices/) _2015-12-07_
  * [A Weekend with Go, Beego and React](http://foreman-shlomizadok.rhcloud.com/2015/11/03/a-weekend-with-go-lang-beego-react/) _2015-11-03_
  * [HTTP Session Handling on Heroku](https://devcenter.heroku.com/articles/go-sessions) _2015-09-09_
  * [Go Resiliency Patterns](https://github.com/eapache/go-resiliency) _2015-09-01_
  * [http.Handler and Error Handling in Go](https://elithrar.github.io/article/http-handler-error-handling-revisited/) _2015-07-02_
  * [Deploy a golang photo archive tool to the cloud on IBM BlueMix](http://www.ibm.com/developerworks/cloud/library/cl-golang-photo-archive-bluemix/index.html) _2015-06-05_
  * [A Journey into Microservices - Part 1](https://sudo.hailoapp.com/services/2015/03/09/journey-into-a-microservice-world-part-1/), [Part 2](https://sudo.hailoapp.com/services/2015/03/09/journey-into-a-microservice-world-part-2/), [Part 3](https://sudo.hailoapp.com/services/2015/03/09/journey-into-a-microservice-world-part-3/) _2015-03_09_
  * [Making a RESTful JSON API in Go](http://thenewstack.io/make-a-restful-json-api-go/) _2015-01-01_
  * [Building a Web Server in Go](http://thenewstack.io/building-a-web-server-in-go/) _2014-09-01_
  * [Painless Web Handlers in Go](http://shadynasty.biz/blog/2012/08/07/painless-web-handlers-in-go/) _2012-08-07_
  * [Implementing Chat with WebSockets](http://gary.beagledreams.com/page/go-websocket-chat.html) _2012-03-22_


## Misc

  * [Go-powered Open Source IoT Integration Framework "Flogo"](http://www.kai-waehner.de/blog/2016/11/03/open-source-project-flogo-overview/) _2016-11-07_
  * [Build Slack Slash Commands with Go](http://www.programmableweb.com/news/how-to-use-slack-api-to-build-slash-commands-powered-google-app-engine-and-go/how-to/2015/09/16) _2015-09-15_
  * [String Matching by Damian Gryski](http://blog.gopheracademy.com/advent-2014/string-matching/) _2014-12-05_
  * [State machines in Go (#golang)](http://denis.papathanasiou.org/?p=1190) _2013-02-10_
  * [Go & Assembly](http://www.doxsey.net/blog/go-and-assembly) _2013-02-05_
  * [Function Types in Go (golang)](http://jordanorelli.tumblr.com/post/42369331748/function-types-in-go-golang) _2013-02-05_
  * [Optimizing Real World Go](http://bpowers.github.com/weblog/2013/01/05/optimizing-real-world-go/) _2013-01-05_
  * [Methods as Objects in Go](http://ernestmicklei.com/2012/11/26/methods-as-objects-in-go/) _2012-12-26_
  * [Applying The Clean Architecture to Go applications](http://manuel.kiessling.net/2012/09/28/applying-the-clean-architecture-to-go-applications/) _2012-09-08_
  * [An introduction to cross compilation with Go](http://dave.cheney.net/2012/09/08/an-introduction-to-cross-compilation-with-go) _2012-09-08_
  * [Function Call by Name in Golang](http://www.mikespook.com/2012/07/function-call-by-name-in-golang/) _2012-07-05_
  * [Using the Go Regexp Package](http://blog.kamilkisiel.net/blog/2012/07/05/using-the-go-regexp-package/) _2012-07-05_
  * [Zero Downtime upgrades of TCP servers in Go](http://blog.nella.org/?p=879) _2012-05-29_
  * [Go Reflection Codex](http://jimmyfrasche.github.io/go-reflection-codex/)
  * [Go JSON Marshalling and Unmarshalling cheatsheet](https://eager.io/blog/go-and-json/) _2015-09-30_


## Chinese
  * [How to write Go code](http://chenxiaoyu.org/2012/03/14/howto-write-golang-code.html)
  * [Test Go module](http://chenxiaoyu.org/2012/12/07/golang-module-test-benchmark.html)
  * [Build web application with golang](https://github.com/astaxie/build-web-application-with-golang)
  * [Go语言评估报告](https://docs.google.com/document/d/1NosYIbM6tfBqKh49BrHOngBfXuT1MfrvYXwc_ikwuMk/edit)
  * [Why you PHP guys should learn Golang](http://www.mikespook.com/2012/08/%e4%b8%ba%e4%bb%80%e4%b9%88phper%e5%ba%94%e5%bd%93%e5%ad%a6%e4%b9%a0golang/)
  * [Function Call by Name in Golang](http://www.mikespook.com/2012/07/%e5%9c%a8-golang-%e4%b8%ad%e7%94%a8%e5%90%8d%e5%ad%97%e8%b0%83%e7%94%a8%e5%87%bd%e6%95%b0/)
  * [Golang: Funny Play with Channel](http://www.mikespook.com/2012/06/golang-channel-%e6%9c%89%e8%b6%a3%e7%9a%84%e5%ba%94%e7%94%a8/)
  * [Using MyMySQL - A interface of database/sql](http://www.mikespook.com/2012/05/mymysql-%e7%9a%84-databasesql-%e6%8e%a5%e5%8f%a3%e4%bd%bf%e7%94%a8/)
  * [Go did What on the Stack?](http://www.mikespook.com/2011/03/go%e5%9c%a8stack%e4%b8%8a%e5%b9%b2%e4%ba%86%e7%a5%9e%e9%a9%ac%ef%bc%9f/)
  * [Gobs on the wire (Translation)](http://www.mikespook.com/2011/03/%e7%bf%bb%e8%af%91%e9%a3%9e%e7%bf%94%e7%9a%84-gob/)
  * [Go Environment Setup (Translation)](http://www.mikespook.com/2012/02/%E7%BF%BB%E8%AF%91go-%E7%8E%AF%E5%A2%83%E8%AE%BE%E7%BD%AE/)
  * [Error Handling and Go (Translation)](http://www.mikespook.com/2011/08/%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86%E5%92%8Cgo/)
  * [The Go Tool (Translation)](http://www.mikespook.com/2012/02/%E7%BF%BB%E8%AF%91go-%E5%B7%A5%E5%85%B7/)
  * [Less is exponentially more (Translation)](http://www.mikespook.com/2012/06/%E7%BF%BB%E8%AF%91%E5%B0%91%E6%98%AF%E6%8C%87%E6%95%B0%E7%BA%A7%E7%9A%84%E5%A4%9A/)
  * [Zero Downtime upgrades of TCP servers in Go (Translation)](http://www.mikespook.com/2012/05/%E7%BF%BB%E8%AF%91%E7%94%A8-go-%E5%AE%9E%E7%8E%B0%E9%9B%B6%E5%81%9C%E6%9C%BA%E5%8D%87%E7%BA%A7-tcp-%E6%9C%8D%E5%8A%A1/)

## Czech
  * [Google Go - 1st birthday](http://www.abclinuxu.cz/clanky/google-go-1.-narozeniny)
  * [Google Go - what we find in the kit](http://www.abclinuxu.cz/clanky/google-go-co-najdeme-ve-stavebnici)
  * [Google Go - advanced topics](http://www.abclinuxu.cz/clanky/google-go-pokrocilejsi-temata)
  * [Google Go by examples I.](http://www.abclinuxu.cz/clanky/google-go-v-prikladech-1)
  * [Google Go by examples II.](http://www.abclinuxu.cz/clanky/google-go-v-prikladech-2)
  * [Error handling in Go](http://www.abclinuxu.cz/clanky/osetrovani-chyb-v-go)
  * [Google Go - The Laws of Reflection](http://www.abclinuxu.cz/clanky/google-go-pravidla-reflexe)
  * [Google Go - 2nd birthday](http://www.abclinuxu.cz/clanky/google-go-2.-narozeniny)

## German
  * [Der GoLang-Spicker](https://archium.org/Golang#Ein_Go-Spickzettel_.28zu_deutsch_.22Cheat_Sheet.22.29) _2018-08-30_
  * [Programmiersprachen im Multicore Zeitalter - Google GO und Nebenläuﬁgkeit](http://ps.informatik.uni-siegen.de/downloads/Seminare/multicore-ws2011/donner.pdf) ` [PDF] ` _2012-02-02_
  * [A list of German press articles about Go](http://www.hweidner.de/redmine/projects/pub/wiki/Golang_Presse)

## Japanese
  * [WindowsでGo言語のまとめ](http://esten.wankuma.com/)
  * [Go言語で jQuery ライクな操作が出来る goquery を試した。](http://mattn.kaoriya.net/software/lang/go/20120914184828.htm)
  * [Go言語向けの ORM、gorp がなかなか良い](http://mattn.kaoriya.net/software/lang/go/20120914222828.htm)
  * [GAE/GでGoogle Cloud Storageを利用するには（１）](http://takashi-yokoyama.blogspot.jp/2012/08/gaeggoogle-cloud-storage.html)
  * [Go言語のWebフレームワーク"goweb"をGAE/Gで動かす](http://takashi-yokoyama.blogspot.jp/2012/07/gowebgowebgaeg.html)
  * [Ubuntu 12.04にgolangを”ソースから”インストールする。](http://takashi-yokoyama.blogspot.jp/2012/07/ubuntu-1204golang.html)
  * [GAE/Gで時間のチェック（Datastore編）](http://takashi-yokoyama.blogspot.jp/2012/06/gaegdatastore.html)

## Korean
  * [The Go Programming Language](http://www.slideshare.net/golanger/abou-go)
  * [You can read Go code](http://goo.gl/vUeSzl)
  * [Go channel tutorial](http://blog.sabzil.org/2014/12/golang-channels-tutorial)
  * [Go character encoding](http://www.slideshare.net/suapapa/go-character-encoding)
  * [Using Google API in Go](http://www.slideshare.net/golanger/using-google-api-in-go)
  * [Go로 Git 들여다보기](http://goo.gl/nCDV3I)
  * [Go: 90% 완벽?!, 100% of the time 슬라이드 번역 ](http://100coding.com/go/slide)
  * [Go 동시성 패턴 advanced 영상 번역](http://www.youtube.com/watch?v=4g2skln42eo)
  * [Go + Revel + Gorp 간단 게시판 만들기](http://100coding.com/go/tutorial/1)
  * [Go + Revel + Gorm 으로 만드는 블로그](https://github.com/jaehue/goblog/wiki/Hello-World)