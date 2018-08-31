# Go 2 Generics Feedback

This page is meant to collect and organize feedback about the Go 2 [contracts (generics) draft design](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md).

Please post feedback on your blog, Medium, GitHub Gists, mailing lists, Google Docs, etc. And then please link it here.

As the amount of feedback grows, please feel free to organize this page by specific kind of feedback.

 - Liam Breck, “[Please Don't Mangle the Function Signature](https://gist.github.com/networkimprov/7c1f311f26852bc912765e4110af062b)”, August 2018

- DeedleFake, "[Feedback for Go 2 Design Drafts](https://deedlefake.com/2018/08/feedback-for-go-2-design-drafts/)", August 2018

- Roberto (empijei) Clapis, "[Hard to read syntax](https://gist.github.com/empijei/a9665ac5e3059671be229acee8826798)", August 2018

- Richard Fliam, "[Go2 Generics Let You Construct the Natural Numbers](https://gist.github.com/rfliam/c806a4300aa97f2762295ef97d3e924f)", August 2018

 - Emily Maier, "[Getting specific about generics](https://emilymaier.net/words/getting-specific-about-generics/)", August 2018

 - Roger Peppe, "[Go generics feedback](https://gist.github.com/rogpeppe/2be10112c9d875afc0c85effc5595a09), August 2018

 - Ruan Kunliang, "[Package level generics](https://gist.github.com/PeterRK/41d4d3f54b8db55cd616403fd5a389f3)", August 2018

 - Javier Zunzunegui, "[Compiling Generics](https://gist.github.com/JavierZunzunegui/7032f5846fd255811e7af39bd2c74f38)", August 2018

 - jimmy frasche, "[Embedding of type parameters should not be allowed](https://github.com/golang/go/issues/15292#issuecomment-417422599)", August 2018

 - _Your Name_, “[_Title_](#URL)”, _month year_

 - etc.


## Quick comments

 - [Bodie Solomon](https://github.com/binary132): I find the generics design a bit confusing and opaque.  Please consider integrating some concepts from [Zig's beautiful comptime functions](https://news.ycombinator.com/item?id=13761571)!  The design of Go 2 generics is clever, but I feel it goes against Go's traditional tight coupling between simple runtime semantics and simple syntax.  Additionally, one of the biggest problems of Go, which prevents it from being a viable competitor everywhere I might like to use it, is that I cannot be rid of the GC and runtime.  It was my strong hope that Go 2 would introduce compile-time-only generics such that I could reliably avoid the use of dynamic interfaces where I don't want them, without relying on codegen.  Unfortunately it looks like that will be decided by the compiler without my input.  Please, at least, consider giving users the ability to constrain generics to compile-time-only resolution, perhaps as a property of a Contract, rejecting compilation of dynamic types to satisfy the contract.

 - Dag Sverre Seljebotn: C++ has a huge problem with people abusing metaprogramming ("generics") to do compile-time metaprogramming. I really wished Go had gone down the path of Julia, which offers hygienic macros. Even if it is kept strictly at a compile-time barrier and no run-time code generation, this would at least avoid all the bad tendencies we see in the C++ world that comes from their templating system. Things you can do with generics you can usually pull off with macros too (e.g., `SortSliceOfInts = MakeSliceSorterFunctionMacro!(int)` could generate a new function to sort a slice of integers). Link: https://docs.julialang.org/en/v0.6.1/manual/metaprogramming/

 - Maxwell Corbin: The issues raised in the Discussion and Open Questions section all could be avoided by defining generics at the package rather than the function or type level. The reason for this is simple: types can reference themselves, but packages can't import themselves, and while there are many ways to algorithmically generate more type signatures, you cannot do the same with import statements. A quick example of such syntax might be:
    
    ```go
    \\ list
    package list[T]
    
    type T interface{}
    
    type List struct {
        Val T
        Next *List
    }
    
    // main
    package main
    
    import (
        il "list"[int]
        sl "list"[string]
    )
    
    var iList = il.List{3}
    var sList = sl.List{"hello"}
    
    // etc...
    ```
    
    The syntax in the example is probably needlessly verbose, but the point is that none of the unfortunate code examples from the blog post are even legal constructions. Package level generics avoids the most abusive problems of meta-programming while retaining the bulk of its usefulness.

 - Andrew Gwozdziewycz: The use of the word `contract` gives me pause due to it overloading "contract" as in [Design by Contract](https://en.wikipedia.org/wiki/Design_by_contract). While the generics use case has some similarities with the "contracts" in DbC if you squint a bit, the concepts are quite different. Since "contracts" are an established concept in Computer Science, I think it would be far less confusing to use a different name like `behavior` or `trait`. The design document also suggests reasons why using `interface` is not ideal, though, Go's contract mechanism seems too obvious an extension of interfaces to disregard so quickly... If it can be done `interface setter(x T) { x.Set(string) error }` and `interface addable(x T, y U) { x + y }` seem quite natural to read and understand. 

    - Russell Johnston: Agreed that it would be great to merge contracts and interfaces. Another way around the operator-naming problem might be to provide some standard interfaces for the operators, with bodies inexpressible in normal Go code. For example, a standard `Multipliable` interface would allow the `*` and `*=` operators, while a standard `Comparable` interface would allow `==`, `!=`, `<`, `<=`, `>=`, and `>`. To express operators with multiple types, these interfaces would presumably need type parameters themselves, for example: `type Multipliable(s Self /* this exists implicitly on all interfaces */, t Other) interface { /* provided by the language */ }`. Then user-written interfaces/contracts could use these standard identifier-based names, neatly sidestepping the issues mentioned in the design document around syntax and types.
    - Roberto (empijei) Clapis: I agree on this and on the fact that it should be clearer where to use interfaces and where to use contracts. Unifying the two would be great, as they try to address overlapping issues.
    - Kurnia D Win: I think `constraint` is better keyword than `contract`. Personally i like `type addable constraint(x T, y U) { x + y }` instead of merging with interface.

- Hajime Hoshi: I feel like the supposed proposal is too huge to the problems we want to solve listed at https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md . I'm worried this feature would be abused and degrade readability of code. Sorry if I am missing, but the proposal doesn't say anything about `go generate`. Wouldn't `go generate` be enough to the problems?

- Stephen Rowles: I find the method syntax hard to parse, as a human reading it, it might be clearer to use a different type of enclosing brackets for the type section, e.g.

   ```
   func Sum<type T Addable>(x []T) T {
       var total T
       for _, v := range x {
           total += v
       }
       return total
   }
   ```
   - Roberto Clapis: Please read [this section](https://go.googlesource.com/proposal/+/master/design/go2draft-contracts.md#why-not-use-like-c_and-java)
      - Seems like a bit of a cop-out tbh. It says "in general" which means there must already be exceptions. Go has a nice clear syntax making code simple to read and easy for teams to collaborate. I think it would be worth making the parser more complicated for the sake of making the code readability better. For large scale and long running project readability of the code, and hence maintainability, is king
      - What about [this](https://gist.github.com/empijei/a9665ac5e3059671be229acee8826798)

- Seebs: [Feedback a bit long to inline](https://gist.github.com/seebs/8f943b8b15a8c63c28c7f6f4e5ca6c53), August 2018. Summary basically "I would like a way to specify one contract for each of two types rather than one contract for both types", and "I would prefer `map[T1]T2` to `t1var == t1var` as a canonical form of "T1 must be an allowable map key".

- Sean Quinlan: I find the contract syntax quite confusing. For something that is supposed to defined exactly what is needed and will be part of the documentation of an api, it can contain all sorts of cruft that does not impact the contract. Moreover, to quote from the design: "We don’t need to explain the meaning of every statement that can appear in a contract body". That seems like the opposite of what I would want from a contract. The fact one can copy the body of a function into a contract and have it work seems like a bug to me, not a feature. Personally, I would much prefer a model that unifies interfaces and contracts. Interfaces feel much closer to what I would like a contract to look like and there is a lot of overlap. It seems probable that many contracts will also be interfaces?

- Nodir Turakulov: Please elaborate 
  > Packages like container/list and container/ring, and types like sync.Map, will be updated to be compile-time type-safe.

  and

  > The math package will be extended to provide a set of simple standard algorithms for all numeric types, such as the ever popular Min and Max functions.

  or ideally add a section about transition/migration of existing types/funcs to use type polymorphism.
  FWIU adding type parameter(s) to an existing type/func most likely breaks an existing program that uses the type/func.
  How exactly will `math.Max` be changed?
  Is the intention to make backward-incompatible changes and write tools to automatically convert code to Go2?
  What is the general recommendation for authors of other libraries that provide funcs and types that currently operate with `interface{}`?
  Were default values for type parameters considered? e.g. type parameter for `math.Max` would default to `float64` and type parameter for `"container/list".List` would default to `interface{}`

- Ward Harold: If only for the sake of completeness the [Modula-3](https://www.cs.purdue.edu/homes/hosking/m3/reference/generics.html) generics design should be incorporated into the [Designs in Other Languages](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md#designs-in-other-languages) section. Modula-3 was a beautiful language that sadly got introduced at the wrong time.

- Ole Begemann: You write on the [Generics Overview page](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md): "Swift added generics in Swift 4, released in 2017." This is not true. Swift has had generics since its first public release in 2014. Evidence (just one example of many): [a transcript of an Apple developer talk on Swift from WWDC 2014](https://asciiwwdc.com/2014/sessions/404) that talks at length about Swift's generics features.

  This is also incorrect: "`Equatable` appears to be a built-in in Swift, not possible to define otherwise." The `Equatable` protocol is defined in the Swift standard library, but there's nothing special about it. It's totally possible to define the same thing in "normal" code.

- Kevin Gillette: correction for "Contracts" Draft, as of 30 August 2018

  The one instance of `check.Convert(int, interface{})(0, 0)` should instead be `check.Convert(int, interface{})(0)` or provide an explanation as to why it the function should take two zeros instead of one.