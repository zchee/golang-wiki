# Go 2 Generics Feedback

This page is meant to collect and organize feedback about the Go 2 [contracts (generics) draft design](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md).

Please post feedback on your blog, Medium, GitHub Gists, mailing lists, Google Docs, etc. And then please link it here.

As the amount of feedback grows, please feel free to organize this page by specific kind of feedback.

 - \<name\>, “[\<title\>](<link>)”, \<month\> \<year\>
 - \<name\>, “[\<title\>](<link>)”, \<month\> \<year\>
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