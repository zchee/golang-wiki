# Go 2 Generics Feedback

This page is meant to collect and organize feedback about the Go 2 [contracts (generics) draft design](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md).

Please post feedback on your blog, Medium, GitHub Gists, mailing lists, Google Docs, etc. And then please link it here.

As the amount of feedback grows, please feel free to organize this page by specific kind of feedback.

 - \<name\>, “[\<title\>](<link>)”, \<month\> \<year\>
 - \<name\>, “[\<title\>](<link>)”, \<month\> \<year\>
 - etc.


## Quick comments

 - Dag Sverre Seljebotn: C++ has a huge problem with people abusing metaprogramming ("generics") to do compile-time metaprogramming. I really wished Go had gone down the path of Julia, which offers hygienic macros. Even if it is kept strictly at a compile-time barrier and no run-time code generation, this would at least avoid all the bad tendencies we see in the C++ world that comes from their templating system. Things you can do with generics you can usually pull off with macros too (e.g., `SortSliceOfInts = MakeSliceSorterFunctionMacro!(int)` could generate a new function to sort a slice of integers). Link: https://docs.julialang.org/en/v0.6.1/manual/metaprogramming/