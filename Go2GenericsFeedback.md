# Go 2 Generics Feedback

This page is meant to collect and organize feedback about the Go 2 [contracts (generics) draft design](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md).

Please post feedback on your blog, Medium, GitHub Gists, mailing lists, Google Docs, etc. And then please link it here.

As the amount of feedback grows, please feel free to organize this page by specific kind of feedback.

 - Liam Breck, “[Please Don't Mangle the Function Signature](https://gist.github.com/networkimprov/7c1f311f26852bc912765e4110af062b)”, August 2018

- DeedleFake, "[Feedback for Go 2 Design Drafts](https://deedlefake.com/2018/08/feedback-for-go-2-design-drafts/)", August 2018

- Roberto (empijei) Clapis, "[Hard to read syntax](https://gist.github.com/empijei/a9665ac5e3059671be229acee8826798)", August 2018

 - _Your Name_, “[_Title_](#URL)”, _month year_

 - etc.


## Quick comments

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
    - Kurnia D Win: I think `constraint` is better keyword than `contract`.

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