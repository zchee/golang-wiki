---
title: Rangefunc Experiment
---

For a future Go release, the Go team is considering adding range-over function iterators.
Go 1.22 contains a preliminary implementation of the change, enabled by setting `GOEXPERIMENT=rangefunc` when building your program. We invite anyone who wants to help us understand the effects of the change to try using `GOEXPERIMENT=rangefunc` and let us know about any problems or successes encountered.

This page answers frequently asked questions about the change.

### How do I try the change?

Using Go 1.22, build your program using `GOEXPERIMENT=rangefunc`, as in

	GOEXPERIMENT=rangefunc go install my/program
	GOEXPERIMENT=rangefunc go build my/program
	GOEXPERIMENT=rangefunc go test my/program
	GOEXPERIMENT=rangefunc go test my/program -bench=.
	...

This will allow import of the experimental package `iter` which exports types

	type Seq[V any] func(yield func(V) bool)
	type Seq2[K, V any] func(yield func(K, V) bool)

and helper functions

	func Pull[V any](seq Seq[V]) (next func() (V, bool), stop func())
	func Pull2[K, V any](seq Seq2[K, V]) (next func() (K, V, bool), stop func())

With `GOEXPERIMENT=rangefunc` enabled, loops of the form

	for v := range f { ... }    // f has type Seq[V], v has type V
	for k, v := range g { ... } // g has type Seq2[K,V], k and v have types K and V

will iterate over the values provided by `f` and `g`, with the usual semantics for break,
continue, return, and other control flow in the loop bodies.  If `next(v)` or `next(k,v)`
returns false, the range function should stop iterating and return.
The types for `k` and `v` are inferred in the usual way.

### What is a simple example of how range over function runs?

Consider this function for iterating a slice backwards:

	package slices

	func Backward[E any](s []E) func(func(int, E) bool) {
		return func(yield func(int, E) bool) {
			for i := len(s)-1; i >= 0; i-- {
				if !yield(i, s[i]) {
					return
				}
			}
		}
	}

It can be invoked as:

	s := []string{"hello", "world"}
	for i, x := range slices.Backward(s) {
		fmt.Println(i, x)
	}

This program would translate inside the compiler to a program more like:

	slices.Backward(s)(func(i int, x string) bool {
		fmt.Println(i, x)
		return true
	})

The "return true" at the end of the body is the implicit "continue" at the end of the loop body. An explicit continue would translate to "return true" as well. A break statement would translate to "return false" instead. Other control structures are more complicated but still possible.

### How is `iter.Pull` used?

Function iterators are normally "push" iterators where a value generator
(typically a data structure visitor) "pushes" values at a function generated
from the body of the loop.  In some cases it is more convenient to "pull"
values from the value generator, and `iter.Pull` accomplishes that.
In this example, `Zip` combines two range functions into a single range
function that provides the respective pairs from the two inputs:

	// Zipped holds values from an iteration of a Seq returned by [Zip].
	type Zipped[T1, T2 any] struct {
		V1  T1
		OK1 bool

		V2  T2
		OK2 bool
	}

	// Zip returns a new Seq that yields the values of seq1 and seq2 simultaneously.
	func Zip[T1, T2 any](seq1 iter.Seq[T1], seq2 iter.Seq[T2]) iter.Seq[Zipped[T1, T2]] {
		return func(yield func(Zipped[T1, T2]) bool) {
			p1, stop := iter.Pull(seq1)
			defer stop()
			p2, stop := iter.Pull(seq2)
			defer stop()

			for {
				var val Zipped[T1, T2]
				val.V1, val.OK1 = p1()
				val.V2, val.OK2 = p2()
				if (!val.OK1 && !val.OK2) || !yield(val) {
					return
				}
			}
		}
	}

### What will idiomatic APIs with range functions look like?

We don't know yet, and that's really part of the eventual standard library proposal. However, you could imagine a container like a binary tree implementing an All method that returns an iterator:

	func (t *Tree[V]) All() iter.Seq[V]

We would like to establish a name like that, probably All, as the default "all items" iterator. Specific containers might provide others as well. Maybe a list would provide backward iteration too:

	func (l *List[V]) All() iter.Seq[V]
	func (l *List[V]) Backward() iter.Seq[V]

These examples are meant to show that the library can be written in a way that should make these kinds of functions readable and understandable.

### How are more complicated loops implemented?

Beyond simple break and continue, other control flow (labeled break, continue, goto out of the loop, return) requires setting a variable that the code outside the loop can consult when the loop breaks. For example a "return" might turn into something like "doReturn = true; return false" where the "return false" is the "break" implementation, and then when the loop finishes, other generated code would do "if(doReturn) return".

The full rewrite is explained at the top of [cmd/compile/internal/rangefunc/rewrite.go](https://go.googlesource.com/go/+/refs/changes/41/510541/7/src/cmd/compile/internal/rangefunc/rewrite.go) in the implementation.

### What if the iterator function ignores yield returning false?

For range-over-function loops, the yield function generated for the body checks if it is called after it has returned false or after loop itself has exited.  In either case, it will panic.

### Why are yield functions limited to at most two arguments?

There has to be a limit; otherwise people file bugs against the compiler when it rejects ridiculous programs. If we were designing in a vacuum, perhaps we would say it was unlimited but that implementations only had to allow up to 1000, or something like that.

However, we are not designing in a vacuum: go/ast and go/parser exist, and they can only represent and parse up to two range values. We clearly need to support two values to simulate existing range usages. If it were important to support three or more values, we could change those packages, but there does not appear to be a terribly strong reason to support three or more, so the simplest choice is to stop at two and leave those packages unchanged. If we find a strong reason for more in the future, we can revisit that limit.

Another reason to stop at two is to have a more limited number of function signatures for general code to define. Standard library changes are explicitly out of scope for this proposal, but having only three signatures means a package can easily define names for all three, like perhaps:

	package iter

	type Seq0 func(yield func() bool) bool
	type Seq[V any] func(yield func(V) bool) bool
	type Seq2[K, V any] func(yield func(K, V) bool) bool

### What do stack traces look like in the loop body?

The loop body is called from the iterator function, which is called from the function in which the loop body appears. The stack trace will show that reality. This will be important for debugging iterators, aligning with stack traces in debuggers, and so on.

### What happens if the loop body defers a call? Or if the iterator function defers a call?

If a range-over-func loop body defers a call, it runs when the outer function containing the loop returns, just as it would for any other kind of range loop. That is, the semantics of defer do not depend on what kind of value is being ranged over. It would be quite confusing if they did. That kind of dependence seems unworkable from a design perspective. Some people have proposed disallowing defer in a range-over-func loop body, but this would be a semantic change based on the kind of value being ranged over and seems similarly unworkable.

The loop body's defer runs exactly when it looks like it would if you didn't know anything special was happening in range-over-func.

If an iterator function defers a call, the call runs when the iterator function returns. The iterator function returns when it runs out of values or is told to stop by the loop body (because the loop body hit a "break" statement which translated to "return false"). This is exactly what you want for most iterator functions. For example an iterator that returns lines from a file can open the file, defer closing the file, and then yield lines.

The iterator function's defer runs exactly when it looks like it would if you didn't know the function was being used in a range loop at all.

This pair of answers can mean the calls run in a different time order than the defer statements executed, and here the goroutine analogy is useful. Think of the main function running in one goroutine and the iterator running in another, sending values over a channel. In that case, the defers can run in a different order than they were created because the iterator returns before the outer function does, even if the outer function loop body defers a call after the iterator does.

### What happens if the loop body panics? Or if the iterator function panics?

The deferred calls run in the same order for panic that they would in an ordinary return: first the calls deferred by the iterator, then the calls deferred by the loop body and attached to the outer function. It would be very surprising if ordinary returns and panics ran deferred calls in different orders.

Again there is an analogy to having the iterator in its own goroutine. If before the loop started the main function deferred a cleanup of the iterator, then a panic in the loop body would run the deferred cleanup call, which would switch over to the iterator, run its deferred calls, and then switch back to continue the panic on the main goroutine. That's the same order the deferred calls run in an ordinary iterator, even without the extra goroutine.

See [this comment](https://github.com/golang/go/issues/61405#issuecomment-1641050065) for a more detailed rationale for these defer and panic semantics.

### What happens if the iterator function recovers a panic in the loop body?

This is an open question that is not yet decided.

If an iterator recovers a panic from the loop body, the current prototype allows it to invoke yield again and have the loop keep executing. This is a difference from the goroutine analogy. Perhaps it is a mistake, but if so it is a difficult one to correct efficiently. We continue to look into this.

### Can range over a function perform as well as hand-written loops?

Yes. Consider the slices.Backward example again, which first translates to:

	slices.Backward(s)(func(i int, x string) bool {
		fmt.Println(i, x)
		return true
	})

The compiler can recognize that slices.Backward is trivial and inline it, producing:

	func(yield func(int, E) bool) bool {
		for i := len(s)-1; i >= 0; i-- {
			if !yield(i, s[i]) {
				return false
			}
		}
		return true
	}(func(i int, x string) bool {
		fmt.Println(i, x)
		return true
	})

Then it can recognize a function literal being immediately called and inline that:

	{
		yield := func(i int, x string) bool {
			fmt.Println(i, x)
			return true
		}
		for i := len(s)-1; i >= 0; i-- {
			if !yield(i, s[i]) {
				goto End
			}
		}
	End:
	}

Then it can devirtualize yield:

	{
		for i := len(s)-1; i >= 0; i-- {
			if !(func(i int, x string) bool {
				fmt.Println(i, x)
				return true
			})(i, s[i]) {
				goto End
			}
		}
	End:
	}

Then it can inline that func literal:

	{
		for i := len(s)-1; i >= 0; i-- {
			var ret bool
			{
				i := i
				x := s[i]
				fmt.Println(i, x)
				ret = true
			}
			if !ret {
				goto End
			}
		}
	End:
	}

From that point the SSA backend can see through all the unnecessary variables and treats that code the same as

	for i := len(s)-1; i >= 0; i-- {
		fmt.Println(i, s[i])
	}

This looks like a fair amount of work, but it only runs for simple bodies and simple iterators, below the inlining threshold, so the work involved is small. For more complex bodies or iterators, the overhead of the function calls is insignificant.

### Can you provide more motivation for range over functions?

The most recent motivation is the addition of generics, which we expect will lead to custom containers such as ordered maps, and it would be good for those custom containers to work well with range loops.

Another equally good motivation is to provide a better answer for the many functions in the standard library that collect a sequence of results and return the whole thing as a slice. If the results can be generated one at a time, then a representation that allows iterating over them scales better than returning an entire slice. We do not have a standard signature for functions that represent this iteration. Adding support for functions in range would both define a standard signature and provide a real benefit that would encourage its use.

For example, here are a few functions from the standard library that return slices but probably merit forms that return iterators instead:

 - strings.Split
 - strings.Fields
 - bytes variants of the above
 - regexp.Regexp.FindAll and friends

There are also functions we were reluctant to provide in slices form that probably deserve to be added in iterator form. For example, there should be a strings.Lines(text) that iterates over the lines in a text.

Similarly, iteration over lines in a bufio.Reader or bufio.Scanner is possible, but you have to know the pattern, and the pattern is different for those two and tends to be different for each type. Establishing a standard way to express iteration will help converge the many different approaches that exist today.

For additional motivation for iterators, see [#54245](https://go.dev/issue/54245). For additional motivation specifically for range over functions, see [#56413](https://go.dev/issue/56413).

### Will Go programs using range over functions be readable?

We think they can be. For example using slices.Backward instead of the explicit count-down loop should be easier to understand, especially for developers who don't see count-down loops every day and have to think carefully through the boundary conditions to make sure they are correct.

It is true that the possibility of range over a function means that when you see range x, if you don't know what x is, you don't know exactly what code it will run or how efficient it will be. But slice and map iteration are already fairly different as far as the code that runs and how fast it is, not to mention channels. Ordinary function calls have this problem too - in general we have no idea what the called function will do - and yet we find ways to write readable, understandable code, and even to build an intuition for performance.

The same will certainly happen with range over functions. We will build up useful patterns over time, and people will recognize the most common iterators and know what they do.

### Why are the semantics not exactly like if the iterator function ran in a coroutine or goroutine?

Running the iterator in a separate coroutine or goroutine is more expensive and harder to debug than having everything on one stack. Since we're going to have everything on one stack, that fact will change certain visible details. We just saw the first: stack traces show the calling function and the iterator function interleaved, as well as showing the explicit yield function that does not exist on the page in the program.

It can be helpful to think about running the iterator function in its own coroutine or goroutine as an analogy or mental model, but in some cases the mental model doesn't give the best answer, because it uses two stacks, and the real implementation is defined to use one.

