This page links to resources for learning about concurrency in Go.  The items are presented in order, from beginner material to advanced topics.

## Beginner
- Read [Effective Go: Concurrency](https://go.dev/doc/effective_go#concurrency)
- Watch [Simulating a real-world system in Go](https://www.dotconferences.com/2017/11/sameer-ajmani-simulating-a-real-world-system-in-go)
- Study [The Go Programming Language Specification](https://go.dev/ref/spec), especially
    - [Go statements](https://go.dev/ref/spec#Go_statements)
    - [Channel types](https://go.dev/ref/spec#Channel_types)
    - [Send statements](https://go.dev/ref/spec#Send_statements)
    - [Receive operator](https://go.dev/ref/spec#Receive_operator)
    - [Select statements](https://go.dev/ref/spec#Select_statements)
- Code [A Tour of Go: Concurrency](http://tour.golang.org/concurrency/1)
- Read the [Frequently Asked Questions (FAQ)](https://go.dev/doc/faq), especially
    - [Why build concurrency on the ideas of CSP?](https://go.dev/doc/faq#csp)
    - [Why goroutines instead of threads?](https://go.dev/doc/faq#goroutines)
    - [Why are map operations not defined to be atomic?](https://go.dev/doc/faq#atomic_maps)
    - [What operations are atomic? What about mutexes?](https://go.dev/doc/faq#What_operations_are_atomic_What_about_mutexes)
    - [Why doesn't my program run faster with more CPUs?](https://go.dev/doc/faq#parallel_slow)
    - [How can I control the number of CPUs?](https://go.dev/doc/faq#number_cpus)
    - [What happens with closures running as goroutines?](https://go.dev/doc/faq#closures_and_goroutines)

## Intermediate
- Study [Go by Example](https://gobyexample.com) from [goroutines](https://gobyexample.com/goroutines) through [stateful goroutines](https://gobyexample.com/stateful-goroutines)
- Watch [Go Concurrency Patterns](https://talks.golang.org/2012/concurrency.slide#1)
- Watch [A Practical Guide to Preventing Deadlocks and Leaks in Go](https://www.youtube.com/watch?v=3EW1hZ8DVyw)
- Read [Share Memory By Communicating](https://go.dev/blog/share-memory-by-communicating) and do the [codewalk](https://go.dev/doc/codewalk/sharemem/)
- Read [Go Concurrency Patterns: Timing out, moving on](https://go.dev/blog/go-concurrency-patterns-timing-out-and)
- Watch [Concurrency is not Parallelism](http://talks.golang.org/2012/waza.slide#1)
- Read [Go Concurrency Patterns: Pipelines and Cancellation](https://go.dev/blog/pipelines)
- Read [Rethinking Classical Concurrency Patterns](https://github.com/golang/go/wiki/Go-Community-Slides#rethinking-classical-concurrency-patterns)
- Study [Package sync](https://pkg.go.dev/sync/)
- Read [Introducing the Go Race Detector](https://go.dev/blog/race-detector)
- Watch [Go: code that grows with grace](http://talks.golang.org/2012/chat.slide#1)
- Read [Mutexes and Semaphores Demystified](http://www.barrgroup.com/Embedded-Systems/How-To/RTOS-Mutex-Semaphore)

## Advanced
- Watch [Advanced Go Concurrency Patterns](https://go.dev/blog/advanced-go-concurrency-patterns)
- Read [Advanced Go Concurrency Patterns](http://talks.golang.org/2013/advconc.slide#1)
- Read [Go Concurrency Patterns: Context](https://go.dev/blog/context)
- Study [The Go Memory Model](https://go.dev/ref/mem)
- Study [Package atomic](https://pkg.go.dev/sync/atomic/)
- Read [Principles of Designing Go APIs with Channels](https://inconshreveable.com/07-08-2014/principles-of-designing-go-apis-with-channels/)
- Read [Advanced Go Concurrency Primitives](https://encore.dev/blog/advanced-go-concurrency)
- Watch [The Scheduler Saga](https://www.youtube.com/watch?v=YHRO5WQGh0k)
- Read [The Scheduler Saga](https://speakerdeck.com/kavya719/the-scheduler-saga)
- Watch [Understanding Channels](https://www.youtube.com/watch?v=KBZlN0izeiY)
- Read [Understanding Channels](https://speakerdeck.com/kavya719/understanding-channels)