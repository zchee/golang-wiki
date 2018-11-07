# Go 2 Generics Feedback

This page is meant to collect and organize feedback about the Go 2 [contracts (generics) draft design](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md).

Please post feedback on your blog, Medium, GitHub Gists, mailing lists, Google Docs, etc. And then please link it here.

As the amount of feedback grows, please feel free to organize or reorganize this page by specific kind of feedback.

## Supporting

- Roger Peppe, "[Go contracts use case: generic mgo](https://gist.github.com/rogpeppe/cbbaf2521749717137625e33ba203eed)", September 2018

- Richard Fliam, "[Go2 Generics Let You Construct the Natural Numbers](https://gist.github.com/rfliam/c806a4300aa97f2762295ef97d3e924f)", August 2018

- Roger Peppe, "Go generics at runtime", [Part 1](https://gist.github.com/rogpeppe/f9216e5f2b1c99fc13108825dbda6181), [Part 2](https://gist.github.com/rogpeppe/9fa9a267472fb80e9ddc4a940aa26e14), September 2018

## Supplemental (supporting with modifications)

- alanfo, "[Proposed changes to the Go draft generics design in the light of feedback received](https://gist.github.com/alanfo/72f07362d687f625a958bde1808e0c87)", October 2018

- Andy Balholm "[Enumerated and structural contracts](https://gist.github.com/andybalholm/8165da83c10a48e56590c96542e93ff2)", October 2018

- Burak Serdar "[Types are contracts](https://gist.github.com/bserdar/8f583d6e8df2bbec145912b66a8874b3)", October 2018

- Patrick Smith, "[Go generics for built-in and user-defined type parameters](https://gist.github.com/pat42smith/ed63aca983d4ba14fdfa320296211f40)", September 2018

- Jacob Carlborg, "[Go 2 draft D corrections](https://gist.github.com/jacob-carlborg/b3c91a94f306564158b2a6ac58a57d50)", September 2018

- alanfo, "[A simplified generics constraint system](https://gist.github.com/alanfo/fb2438f376dac0db3be5664702f39aab)", September 2018

- Paul Borman, "[Simplifying syntax](https://gist.github.com/pborman/a6958ee6b7d6668e35fc99db07ea29e4)", September 2018

- mrwhythat, "[Go 2 generics draft notes](https://gist.github.com/mrwhythat/f5f2e1ea2bb9869082da55529586d972)", September 2018

- Roger Peppe, "[Operator overloading](https://gist.github.com/rogpeppe/0a87ef702189689201ef1d4a170939ac)", September 2018

- Peter McKenzie, "[Alternative generics syntax](https://gist.github.com/peter-mckenzie/5cc6530da1d966e743f4a39c150a6ac2)", September 2018

- Ted Singer, "[The design goal for syntax is to help humans read](https://gist.github.com/TedSinger/9ab1857bdd00d1f3523911362380f901)", September 2018

- alanfo, "[Suggested amendment to Go 2 generics draft design](https://gist.github.com/alanfo/5da5932c7b60fd130a928ebbace1f251)", September 2018

- Dean Bassett, "[If we're going to use contracts, allow unary + on string](https://github.com/golang/go/issues/27657), September 2018"

- Kevin Gillette, "[Regarding the Go 2 Generics Draft](https://medium.com/@xtg/regarding-the-go-2-generics-draft-39f7815be89)", September 2018

- jimmy frasche, "[Embedding of type parameters should not be allowed](https://github.com/golang/go/issues/15292#issuecomment-417422599)", August 2018

- Javier Zunzunegui, "[Compiling Generics](https://gist.github.com/JavierZunzunegui/7032f5846fd255811e7af39bd2c74f38)", August 2018

- Liam Breck, “[Please Don't Mangle the Function Signature](https://gist.github.com/networkimprov/7c1f311f26852bc912765e4110af062b)”, August 2018

- DeedleFake, "[Feedback for Go 2 Design Drafts](https://deedlefake.com/2018/08/feedback-for-go-2-design-drafts/)", August 2018

- Roberto (empijei) Clapis, "[Hard to read syntax](https://gist.github.com/empijei/a9665ac5e3059671be229acee8826798)", August 2018

- Dominik Honnef, "[My thoughts on the Go Generics Draft](http://honnef.co/posts/2018/08/opinions-on-go-generics-draft/)", August 2018

## Counterproposals

- Andy Balholm, "[Contracts and Adaptors](https://gist.github.com/andybalholm/acecba3acf57bf1254142dadce928890)", November 2018

- Patrick Smith, "[Go Generics with Adaptors](https://gist.github.com/pat42smith/ccf021193971f6de6fdb229d68215302)", October 2018

- Ian Denhardt, "[Go Generics: A Concrete Proposal Re: Using Interfaces Instead Of Contracts.](https://gist.github.com/zenhack/ad508d08c72fce6df945a49945ad826d)", October 2018

- Arendtio "[Generics in Go inspired by Interfaces](https://gist.github.com/arendtio/77dd4df5f4b19dc69da350648434a88a)", September 2018

- Scott Cotton, "[Draft Proposal Modification for Unifying Contracts and Interfaces](https://github.com/wsc1/proposal/blob/master/design/go2draft-contracts.md)" ([diff](https://github.com/golang/proposal/compare/master...wsc1:master)), September 2018

- ohir, "[CGG, Craftsman Go Generics](https://github.com/ohir/gonerics)", September 2018

- ~~Dean Bassett, "[Using interfaces instead of contracts](https://gist.github.com/deanveloper/c495da6b9263b35f98b773e34bd41104)", September 2018~~  
  _I have made a second proposal ("contract embedding") listed further down that solves the issues with this one_

- dotaheor, "[Combine contract and code together and view generic as compile-time calls with multiple outputs](https://gist.github.com/dotaheor/4b7496dba1939ce3f91a0f8cfccef927)", September 2018. (Updated from time to time)

- Aleksei Pavliukov, "[Extend type and func keywords](https://github.com/a5i/go-proposal/blob/master/generics.md)", September 2018

- Han Tuo, "[Generic as a kind of types -- type T generic {int, float64}](https://gist.github.com/hantuo/574aeda064c18eb69aa6806fbb259510)", September 2018

- Nate Finch, "[Go2 Contracts Go Too Far](https://npf.io/2018/09/go2-contracts-go-too-far/)", September 2018

- Roger Peppe, "[Go Contracts as type structs](https://gist.github.com/rogpeppe/7ea0cb6037aa520934257bf88a1012c5)", September 2018

- Axel Wagner, "[Scrapping contracts](https://blog.merovius.de/2018/09/05/scrapping_contracts.html)", September 2018

- Matt Sherman "[Generics as built-in typeclasses](https://clipperhouse.com/go-generics-typeclasses/)", September 2018

- Roger Peppe, "[Revised generics proposal](https://gist.github.com/rogpeppe/45f5a7578507989ec4ba5ac639ae2c69)", September 2018

- Steven Blenkinsop, “[Response to the Go2 Contracts Draft Design – Auxiliary Types](https://gist.github.com/stevenblenkinsop/7b967bb98f876b99dc15620f9fda9eb1)”, September 2018

- Dave Cheney, "[Maybe adding generics to Go IS about syntax after all](https://dave.cheney.net/2018/09/03/maybe-adding-generics-to-go-is-about-syntax-after-all)", September 2018

- Christian Surlykke, "[Constraints for Go Generics](https://github.com/surlykke/Go-Generics-with-constraints/tree/V2.0), September 2018"

- Some Gophers on go-nuts, “[Unifying Interfaces and Contracts](https://groups.google.com/forum/#!topic/golang-nuts/aw3XQV8k1Vw)”, August 2018

- Roger Peppe, "[Go generics feedback](https://gist.github.com/rogpeppe/2be10112c9d875afc0c85effc5595a09), August 2018

- Ruan Kunliang, "[Package level generics](https://gist.github.com/PeterRK/41d4d3f54b8db55cd616403fd5a389f3)", August 2018

- Emily Maier, "[Getting specific about generics](https://emilymaier.net/words/getting-specific-about-generics/)", August 2018

- Dean Bassett, "[Contract embedding](https://gist.github.com/deanveloper/9063720344d7a041795cba778d7de77c)", October 2018

## Against

- Tokyo Gophers, "[Comments from Go 2 draft design feedback event](https://docs.google.com/document/d/1O6w4eL6ChROXrJ2vw9IhezzsdG7n8ToMnGnYLRQbjQg/edit?usp=sharing)", October 2018

* Jason Moiron, "[Notes on the Go2 Generics Draft](http://jmoiron.net/blog/notes-on-the-go2-generics-draft)", September 2018

* Yoshiki Shibukawa, "[Feedback for generics/contract proposals](https://gist.github.com/shibukawa/9c9eba1e68c3721f96b6f1456cfc4271), September 2018"

## Adding Your Feedback

Please format all entries as below.

- _Your Name_, “[_Title_](#URL)”, _month year_

To make it easier to see new feedback. Please _make a Gist_. And also help to keep the list sorted in reverse-chronological order by including your new entry at the _top_ of the category list.

## Quick comments

- [Bodie Solomon](https://github.com/binary132): I find the generics design a bit confusing and opaque. Please consider integrating some concepts from [Zig's beautiful comptime functions](https://news.ycombinator.com/item?id=13761571)! The design of Go 2 generics is clever, but I feel it goes against Go's traditional tight coupling between simple runtime semantics and simple syntax. Additionally, one of the biggest problems of Go, which prevents it from being a viable competitor everywhere I might like to use it, is that I cannot be rid of the GC and runtime. It was my strong hope that Go 2 would introduce compile-time-only generics such that I could reliably avoid the use of dynamic interfaces where I don't want them, without relying on codegen. Unfortunately it looks like that will be decided by the compiler without my input. Please, at least, consider giving users the ability to constrain generics to compile-time-only resolution, perhaps as a property of a Contract, rejecting compilation of dynamic types to satisfy the contract.

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

- yesuu: In this example, think of `T` as the parameter name and `type` as the parameter type. Obviously it is more reasonable to put the `type` behind, and contract is followed by `type`, like `chan int`.

  ```go
  func Sum(T type Addable)(x []T) T
  ```

  - Roberto Clapis: Please read [this section](https://go.googlesource.com/proposal/+/master/design/go2draft-contracts.md#why-not-use-like-c_and-java)
    - Seems like a bit of a cop-out tbh. It says "in general" which means there must already be exceptions. Go has a nice clear syntax making code simple to read and easy for teams to collaborate. I think it would be worth making the parser more complicated for the sake of making the code readability better. For large scale and long running project readability of the code, and hence maintainability, is king
    - What about [this](https://gist.github.com/empijei/a9665ac5e3059671be229acee8826798)

- Seebs: [Feedback a bit long to inline](https://gist.github.com/seebs/8f943b8b15a8c63c28c7f6f4e5ca6c53), August 2018. Summary basically "I would like a way to specify one contract for each of two types rather than one contract for both types", and "I would prefer `map[T1]T2` to `t1var == t1var` as a canonical form of "T1 must be an allowable map key".

- Seebs: [What if contracts _were_ just the type-parametric functions?](https://github.com/seebs/notes/blob/master/generics_go2.md). (Sep 1, 2018)

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

  - Matt Holiday: Ditto mentioning the [Alphard](<https://en.wikipedia.org/wiki/Alphard_(programming_language)>) language, which was developed about the same time as CLU and also influenced the Ada design. See Alphard: Form and Content, Mary Shaw, ed., Springer 1991 for the various papers collected with some glue material. Alphard & Ada were my introductions to generic programming. Could Go beat C++ for finally delivering contracts after 40 years of waiting?

- Ole Begemann: You write on the [Generics Overview page](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md): "Swift added generics in Swift 4, released in 2017." This is not true. Swift has had generics since its first public release in 2014. Evidence (just one example of many): [a transcript of an Apple developer talk on Swift from WWDC 2014](https://asciiwwdc.com/2014/sessions/404) that talks at length about Swift's generics features.

  This is also incorrect: "`Equatable` appears to be a built-in in Swift, not possible to define otherwise." The `Equatable` protocol is defined in the Swift standard library, but there's nothing special about it. It's totally possible to define the same thing in "normal" code.

- Kevin Gillette: correction for "Contracts" Draft, as of 30 August 2018

  The one instance of `check.Convert(int, interface{})(0, 0)` should instead be `check.Convert(int, interface{})(0)` or provide an explanation as to why it the function should take two zeros instead of one.

- [Adam Ierymenko](http://adamierymenko.com): I have an idea for doing limited operator overloading in Go that might make this proposal more useful for numeric code. It's big so [I stuck it in a Gist here](https://gist.github.com/adamierymenko/a03a62da1513a8cc2ac4dfac81b44a9f).
  - DeedleFake: I completely agree with the arguments against operator overloading, and I'm quite glad overall that Go doesn't have it, but I also think that the inability to resolve the difference between `a == b` and `a.Equals(b)` via a contract is the biggest problem with the draft design as it currently stands. It means that you'd still wind up writing multiple functions for a fair number of things. Try writing a binary tree, for example. Should you use a contract with `t < t` or `t.Less(t)`? For a sum function, should you use `t + t` or `t.Plus(t)`? I definitely want a solution that doesn't involve operator overloading, though. Maybe there could be a way to specify an adapter that basically says `if a type T, which satisfies contract A but not B, is used for a parameter constrained by contract B, apply this to it in order to get it to satisfy contract B`. Contract B could require a `Plus()` method, for example, while contract A requires the use of `+`, so the adapter automatically attaches a user-specified `Plus()` method to `T` for the duration of its use under that contract.
    - Something that might work with this proposal is an `equal(a, b)` builtin that uses `a.Equals(b)` if it exists and `a == b` otherwise, failing to compile if the type is incomparable (and likewise for other operators). It's too weird to seriously consider but it would work with contracts and allow dodging the asymmetry between types that have operators and those that cannot without introducing operator overloading —jimmyfrasche
    - Another idea would be explicitly overloadable operators: `a + b` is not overloadable, but `a [+] b` can be overloaded. It will use normal + for primitive types, but will use `Operator+()` etc. for objects if those are present. I really do think that generics without some sane form of operator overloading or something like it are a lot less useful to the point that you might as well not even do it. -Adam Ierymenko (original poster)
  - Ian Denhardt: DeedleFake outlines the problems with not having operator overloading well I. I think proposals involving making the overloading "loud" are the wrong idea; instead, we should limit which operators can be overloaded to operators which satisfy these critera:
    1. The operator's semantics can be understood as a method call. Most of the operators on numbers pass this test; `big.Add` is still addition in the sense that we know it from int32, uint64 etc. Examples of operators that fail this test are `&&` and `||`; these are short circuting, which no function or method can replicate. They are fundamentally not methods, no matter how you look at them, and should not be overridable by methods. I think operator overloading gets a bad rap in part because C++ allows you to override _everything_, including crazy stuff like the _comma operator_.
    2. There should be clear use cases for overriding them. Again, arithmetic operators pass this test, along with `<` and friends. Pointer dereferencing passes the first test, but I'm having a hard time coming up with uses for "other types of pointers" that actually seem like a good idea. They are a bit more justifiable in C++, but garbage-collected pointers have basically got you covered.
    3. The normal meaning of the operator should be something that is easy to reason about. For example, pointers are a gnarly source of bugs, and having the possibility that `*foo` is doing something other than reading from a memory address makes an already difficult debugging session that much harder. On the other hand, the possibility that `+` may be a call to `big.Add` is relatively self-contained, and unlikely to cause great confusion.
    4. Finally, the standard library has to set a good example; methods overriding `+` should be conceptually addition, for example. C++ gets off on an utterly wrong foot here by defining what is morally `os.Stdout.ShiftLeft("Hello, World!")`.
- Eltjon Metko: How about specifying the contract after the type identifier inside the function Parameters? This way it can be inferred what T is and we can eliminate the first group of parenthesis.

  ```
  func Sum(x []T:Addable) T {
      var total T
      for _, v := range x {
          total += v
      }
      return total
  }
  ```

- Tristan Colgate-McFarlane: After going back and forward for a while, I've come down in favour of the proposal largely as is. A limited syntax for contracts might be preferable, but I believe it should allow referencing specific fields (not just methods as some have proposed). If anything can be done to make compatible interface and contracts inter-use easier, that would also be nice (though I think maybe no additional specifications are needed. Lastly, I think it is worth considering deprecating interface types. Whilst drastic, contracts essentially also allow specifying behaviour. Any contract restrictions that limit that (such as refering to other types within the package), should probably be lifted. contracts appear to be a strict superset of interfaces, and I am generally against having two overlapping features. A tool to aide in writing interaces should also be considered.

- Patrick Smith: We might consider requiring the type keyword when defining methods on generic types. This makes the code a little more verbose, but clearer and more consistent (now type parameters are always preceded by the type keyword).

  ```
  func (x Foo(type T)) Bar()
  ```

- Patrick Smith: In this example, is `Foo(T)` embedded in `Bar(T)`, or does `Bar(T)` have a method named `Foo`?

  ```
  type Foo(type T) interface {}
  type Bar(type T) interface {
          Foo(T)
  }
  ```

- Xingtao Zhao: There are too many round brackets in the proposal. In the proposal, it is said that "[]" is ambiguous in some cases. While if we use [type T, S contract], there are no ambiguities any more.

- Dave Cheney: The earlier Type Functions proposal showed that a type declaration can support a parameter. If this is correct, then the proposed contract declaration could be rewritten from

  ```
  contract stringer(x T) {
      var s string = x.String()
  }
  ```

  to

  ```
  type stringer(x T) contract {
      var s string = x.String()
  }
  ```

  This supports Roger’s observation that a contract is a superset of an interface. `type stringer(x T) contract { ... }` introduces a new contract type in the same way `type stringer interface { ... }` introduces a new interface type.

  - jimmyfrasche: A contract is not a type, though. You can't have a value that is a `stringer`. You can have a value of a type that is a `stringer`. It's a metatype. A type is a kind of predicate on values. You ask the compiler "is this value a `string`" and it answers yes (allowing compilation to continue) or no (stopping to tell you what went wrong). A contract is a predicate on a vector of types. You ask the compiler two questions. Do these types satisfy this contract? Then: do these values satisfy these types? Interfaces kind of blur these lines by storing a `(type, value)` pair, provided that the type has the appropriate methods. It's simultaneously a type and a metatype. Any generics system that does not use interfaces as the metatypes will unavoidably contain a superset of interfaces. While it is entirely possible to define a generics system that exclusively uses interfaces as the metatypes, that does mean losing the ability to write generic functions that use things that interfaces can't talk about, like operators. You have to limit the questions you can ask about the types to their method sets. (I'm fine with this).