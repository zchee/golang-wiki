# Feedback re Go 2 Error Handling Draft Design

This page is meant to collect and organize feedback and discussion 
started with the Go 2 [error handling draft design](https://go.googlesource.com/proposal/+/master/design/go2draft-error-handling-overview.md).

Please post feedback on your blog, Medium, GitHub Gists, mailing lists, Google Docs, etc. And then please link it here.

Please help categorize the rest of the uncategorized proposals at the bottom.

**Update, June 19, 2019** – Based on this feedback we have posted a [proposal for a try builtin](https://go.dev/design/32437-try-builtin), which produced significant feedback on #32437 ([threaded view here](https://swtch.com/try.html)). 

We've disabled comments on that issue until July 1 to give people time to experiment in their own code. We would very much like to see experience reports about using the general try approach in your own code, including trial conversions with [tryhard](https://github.com/griesemer/tryhard). Thanks!

# Experience with the [“try proposal”](https://go.dev/design/32437-try-builtin)

Add to this list:

- TEMPLATE: Your Name, “[Title](URL)”, Month YYYY

* * *

# Requirements

Discussions of the requirements for a new error handling method.

- Warren Stephens, "[Go 2 `handle` should provide line number, source filename, version](https://github.com/warrenstephens/Go2ErrorHandlingFeedback)", December 2018

- Liam Breck, “[Requirements to Consider for Go 2 Error Handling](https://gist.github.com/networkimprov/961c9caa2631ad3b95413f7d44a2c98a)”, September 2018

 - jimmyfrasche, "[Don't special case error or nil](https://gist.github.com/jimmyfrasche/f2cd6aff16db5e46c577da44ec0cfa72)", September 2018

- Matt Dee "[Error Handling Should Support Custom Error Types](https://gist.github.com/mattdee123/a04f95ef5639489668cafd9c3b675a8c)", August 2018

- Ian Lance Taylor, “[Incomplete list of criteria](https://github.com/golang/go/issues/21161#issuecomment-389380686)” from GitHub proposal discussion, May 2018

- Rob Pike (posted by @matjam) “[Simplicity is Complicated](https://www.youtube.com/watch?v=rFejpH_tAHM)”, December 2015


# In support

This includes supporting the existing chaining/stacking of handlers without changes.

 - Tokyo Gophers, "[In support comments from Go 2 feedback event](https://docs.google.com/document/d/1yTDMP0E9hlJyLnKyr-6XL84RogiiwDnk0fMg9HDOKkc/edit#heading=h.f7ryl4573bu9)", October 2018

 - Adam Bouhenguel "[In support of more declarative error handling](https://gist.github.com/ajbouh/716f8daba40199fe4d4d702704f3dfcc)", August 2018

 - Daniel Theophanes, "[Go 2 Design: Error Handling Net Win](https://docs.google.com/document/d/e/2PACX-1vSq487dLylRHjgtKV42EbTKHW1aHZaaso3MZ4HOG1OS-s8suOnR9WZz6ahzH4Kufs2vwKKDMhoj1_I6/pub)", August 2018

- Alexandru-Paul Copil, "[In Support, with slight modifications and considerations](https://gist.github.com/cpl/54ed073e20f03fb6f95257037d311420)", September 2021

## Example code

Code changed to use the existing proposal.

- Daniel Milde, "[Use check-handle draft syntax in gdu](https://github.com/dundee/gdu/pull/51)", May 2021

- Mateusz Czapliński, "[Converting a fragment of real code with error handling to Go 2 'design draft'](https://gist.github.com/akavel/62d90bdc43088574c638eb3b16301a92)", August 2018

 - Blake Mizerany, “[How best to account for partial writes when using check/handle?](https://gist.github.com/bmizerany/fcd0348bda96edce05a4fc7426e47751)”, August 2018

# Against

Critiques without counter-proposals

- Pasha Osipyants, “[Error handling mechanism using current go possibilities](https://pkg.go.dev/github.com/pashaosipyants/errors)”, February 2019

- Anonymous, “[Go 2 Error Handling Non-Proposal](https://groups.google.com/d/topic/golang-nuts/1McP4_-oOpo/discussion)”, October 2018

- Stripe developers, “[Feedback on Go 2 draft designs](https://groups.google.com/d/msg/golang-nuts/3A_MpcNKg7k/DWiHBLArCAAJ)”, October 2018

- Tokyo Gophers, "[Against comments from Go 2 feedback event](https://docs.google.com/document/d/1yTDMP0E9hlJyLnKyr-6XL84RogiiwDnk0fMg9HDOKkc/edit#heading=h.fy8rnze9tll5)", Oct 2018

- Liam Breck, “[Golang, How dare you handle my checks!](https://medium.com/@mnmnotmail/golang-how-dare-you-handle-my-checks-d5485f991289)”, September 2018

- Nate Finch, "[Handle and Check, Let's Not](https://npf.io/2018/09/check-and-handle/)", September 2018

- Jozef Slezak, "[Use semicolons instead of new keywords: check+handle](https://gist.github.com/jozef-slezak/93a7d9d3d18d3fce3f8c3990c031f8d0)", September 2018

- Shannon Wynter "[Error Handling as it can already be done](https://gist.github.com/freman/0b372e46c72f6a27652538b9930ee851)", August 2018


# Recurring themes

Concepts that appear repeatedly among the suggestions below.

- Invoke handler via assignment, e.g. `v, ? := f()`  
  references:
  [1](https://gist.github.com/oktalz/f04f36a3c2f61af22c7a6e06095d18eb),
  [2](https://gist.github.com/pborman/c69e79690d86dfc5c371f096be22930c),
  [3](http://blog.oldcloudguy.com/2019/04/18/error-handling-in-go-2-draft/),
  [4](https://github.com/rockmenjack/go-2-proposals/blob/master/error_handling.md),
  [5](https://gist.github.com/the-gigi/3c1acfc521d7991309eec140f40ccc2b),
  [6](https://gist.github.com/8lall0/cb43e1fa4aae42bc709b138bda02284e),
  [7](https://gist.github.com/dpremus/3b141157e7e47418ca6ccb1fc0210fc7),
  [8](https://gist.github.com/bserdar/4c728f85ca30de25a433e84ad5a065a1),
  [9](https://gist.github.com/mcluseau/1c20c3973fa3acb544d0505637be8d67),
  [10](https://didenko.github.io/grab/grab_worth_it_0.1.1.html),
  [11](https://github.com/gooid/gonotes/blob/master/inline_style_error_handle.md),
  [12](https://gist.github.com/Kiura/4826db047e22b7720d378ac9ac642027),
  [13](https://github.com/golang/go/issues/27519),
  [14](https://gist.github.com/lldld/bf93ca94c24f172e95baf8c123427ace)

- Invoke one of several handlers by name, e.g. `v := check f() ? name`  
  references:
  [1](https://didenko.github.io/grab/grab_worth_it_0.1.1.html),
  [2](https://gist.github.com/forstmeier/b6c6a6d2f6f2f72a81a076322959c959),
  [3](https://gist.github.com/mcluseau/1c20c3973fa3acb544d0505637be8d67),
  [4](https://gist.github.com/the-gigi/3c1acfc521d7991309eec140f40ccc2b),
  [5](https://gist.github.com/PeterRK/4f59579c1162cdbc28086f6b5f7b4fa2),
  [6](https://gist.github.com/marlonche/4e5d4e5aec0555958ec1f181991325f6),
  [7](https://github.com/alnkapa/Go2ErrorHandlingFeedback/blob/master/README.md),
  [8](https://medium.com/@phlatphrog/handling-more-than-just-errors-in-go-f97c5aa2eac4),
  [9](https://gist.github.com/gregwebs/02479eeef8082cd199d9e6461cd1dab3),
  [10](https://github.com/gooid/gonotes/blob/master/inline_style_error_handle.md),
  [11](https://gist.github.com/spakin/86ea86ca48aefc78b672636914f4fc23),
  [12](https://gist.github.com/morikuni/bbe4b2b0384507b42e6a79d4eca5fc61),
  [13](http://devmethodologies.blogspot.com/2018/10/go-error-handling-using-closures.html),
  [14](https://gist.github.com/bserdar/4c728f85ca30de25a433e84ad5a065a1),
  [15](https://medium.com/@marode/the-return-of-the-return-278b8ae261ab),
  [16](https://gist.github.com/dpremus/3b141157e7e47418ca6ccb1fc0210fc7),
  [17](https://github.com/golang/go/issues/27519)


# Modest revisions
 - Leidong Liu, "[a, b, !checkError := Sub(...)](https://gist.github.com/lldld/bf93ca94c24f172e95baf8c123427ace)", Nov 2019

 - Jin Feng, "[A simplified Go 2 error handling solution with no handler], (https://gist.github.com/jfeng45/416d4ecb42a4df50bebf86ce1c41c668)", July 2019

 - Dave Arnold, "[Move special check keyword to left-hand side of assignment](http://blog.oldcloudguy.com/2019/04/18/error-handling-in-go-2-draft/)", April 2019

 - Rockmen, "[Add handle and ? as syntax sugar maybe](https://github.com/rockmenjack/go-2-proposals/blob/master/error_handling.md)", December 2018

 - Steve Manuel, "[Go 2 `handle` statement to optionally use a type switch](https://github.com/golang/go/issues/28344)", October 2018

- Zlatko Bratkovic, "[In support with tiny change](https://gist.github.com/oktalz/f04f36a3c2f61af22c7a6e06095d18eb)", October 2018

- DeedleFake, "[Possible Solution to `check` Awkwardness with Chained Method Calls](https://gist.github.com/DeedleFake/5e8e9e39203dff4839793981f79123aa)", September 2018

- Yesuu Zhang, "[Pass the check and handle parameters, custom handle](https://github.com/yesuu/go-proposal/blob/master/go2errorhanding.md)", September 2018

 - Viktor Kojouharov, "[Reducing the special casing around the new error design draft](https://gist.github.com/urandom/6519990ef9eb7547e888a5f2da7f1a93)", September 2018

- Aleksei Pavliukov, “[Use a function as a handle parameter](https://github.com/a5i/go-proposal/blob/master/use%20a%20function%20as%20a%20handle%20parameter.md)”, September 2018

- Savino Pio Liguori, "[Feedback for Go2 error handling design](https://gist.github.com/8lall0/cb43e1fa4aae42bc709b138bda02284e)", August 2018

 - Jeffrey Koehler, "[In support of Handle Chaining;  On Check](https://gist.github.com/deef0000dragon1/eb224ce4918d4ec3bdbaedf83a32aeb1)", August 2018

 - Garrus, "[Another style of syntactic sugar on error handling](https://gist.github.com/garrus/5b1f73a7640726c92273700eabed9056)", August 2018

 - Paul Borman, "[Arguments against the Go 2 error handling proposal](https://gist.github.com/pborman/c69e79690d86dfc5c371f096be22930c)", August 2018

 - krhubert, "[Error default handler for tests](https://go.dev/issue/32361)", May 2019

 - Franz, Implement error handling like an invariant check of a variable. when the value changes, a function is called. this can then be used in other situations too. 

- Brandon Heenan, "[Concise, with more obvious control flow](https://github.com/bmheenan/goerr/blob/main/README.md)", May 2021

## Remove handler chaining

- Markus Heukelom, "[proposal: Improve error handing using `guard` and `must` keywords](https://github.com/golang/go/issues/31442)", April 2019

 - Alessandro Arzilli, “[Against check as an operator and handler chains](https://gist.github.com/aarzilli/1a85db632edecc8159505e2c785882ed)”, August 2018

- Simon Howard, “[Go 2 errors response: One Handler Per Function](https://gist.github.com/fragglet/df6c5471771d87b2ad597d2efc57cb3e)”, August 2018

- Eli Bendersky, "[Thoughts on the Go 2 Error Handling proposal](https://gist.github.com/eliben/d0c872054864bfc1110ec761c3c53c47)", September 2018

- Yoshiki Shibukawa, "[Every handles should have return statement](https://gist.github.com/shibukawa/42a9dee400c2f8577b4a763bcb1a5e5f)", September 2018


# Counter-proposals

## Error handling with normal functions

- Azamat Kalberdiev, “[Handling every error with intuitive code](https://gist.github.com/Azamat28/5b2c6f66fc4927a002a2d60044aa9231)”, March 2021

- Andrew Phillips, “[Use closures rather than handlers](http://devmethodologies.blogspot.com/2018/10/go-error-handling-using-closures.html)”, October 2018

 - Taihei Morikuni, "[Use functions as an error handler, Add syntactic sugar to remove duplicated if statement](https://gist.github.com/morikuni/bbe4b2b0384507b42e6a79d4eca5fc61)", September 2018

- Scott Pakin, "[Go 2 error handling based on non-local returns](https://gist.github.com/spakin/86ea86ca48aefc78b672636914f4fc23)", September 2018

- Greg Weber "[Error handling with functions and an error return?](https://github.com/golang/go/issues/27567)", September 2018. Originally linked [gist](https://gist.github.com/gregwebs/02479eeef8082cd199d9e6461cd1dab3).

- Gigi Sayfan, “[Go 2 error handling feedback + alternative solution](https://gist.github.com/the-gigi/3c1acfc521d7991309eec140f40ccc2b)", September 2018

- Ruan Kunliang, "[Simple Error Handling for Go 2](https://gist.github.com/PeterRK/4f59579c1162cdbc28086f6b5f7b4fa2)", August 2018

- Martin Rode, "[The return of the return, Error Handling for Go 2](https://medium.com/@marode/the-return-of-the-return-278b8ae261ab)", November 2018

## Labeled error handlers

- Joe Lapp, "[Local-only throw-catch error handling](https://github.com/golang/go/issues/48896)", October 2021

- Danijel Premus, "[Use existing go labels](https://gist.github.com/dpremus/3b141157e7e47418ca6ccb1fc0210fc7)", December 2018

- Burak Serdar, "[Handler for err declares both err and errHandler, less intrusive labeled error handling](https://gist.github.com/bserdar/4c728f85ca30de25a433e84ad5a065a1)", October 2018

- John Forstmeier, "[Labeled error handling](https://gist.github.com/forstmeier/b6c6a6d2f6f2f72a81a076322959c959)", September 2018

- Mikaël Cluseau, "[Multiple handlers, unambiguous on which return value is used](https://gist.github.com/mcluseau/1c20c3973fa3acb544d0505637be8d67)", September 2018

- Kiura Magomadov, “[Addition to Go2 draft error handling](https://gist.github.com/Kiura/4826db047e22b7720d378ac9ac642027)", September 2018

- Liam Breck, “[The `#id/catch` Error Model](https://github.com/golang/go/issues/27519)”, September 2018

- Marlon Che, "[How about separating check and handle?](https://gist.github.com/marlonche/4e5d4e5aec0555958ec1f181991325f6)", August 2018

## Inlining

- Patrick Kelly, "[handling more than just errors in go](https://medium.com/@phlatphrog/handling-more-than-just-errors-in-go-f97c5aa2eac4)", August 2018

- Vlad Didenko, “[Error Handling with `grab | name()`](https://didenko.github.io/grab/grab_worth_it_0.1.1.html)”, November 2017

- Gooid, “[Inline style error handle(simple unambiguous)](https://github.com/gooid/gonotes/blob/master/inline_style_error_handle.md)”, August 2018

## Use defer

 - Victoria Raymond, “[Force 'check' to return error instead of allowing customized logic](https://gist.github.com/VictoriaRaymond/d70663a6ec6cdc59816b8806dccf7826)”, August 2018

 - Night-walker and daokoder, "[Extend and repurpose defer instead of introducing new syntax](https://github.com/daokoder/dao/issues/191#issuecomment-44784919 )", June 2014

## try/catch/finally syntax

- Mathieu Devos, "[Go2 Error Handling Proposal: Scoped Check/Handle](https://gist.github.com/mathieudevos/2bdae70596aca711e50d1f2ff6d7b7cb)", August 2018

- Rust RFC, “[Trait-Based Exception Handling (wherein `catch` is akin to `try`)](https://github.com/rust-lang/rfcs/blob/master/text/0243-trait-based-exception-handling.md)”, February 2016

- ZhiFeng Hu, "[[Go2ErrorHandling] Go should support Exception handler](https://www.netroby.com/view/3910)", August 2018

- Jan Semmelink, “[if-else-undo-done](https://gist.github.com/jansemmelink/235228a0fb56d0eeba8085ab5f8178f3)”, August 2018

- Vladimir Utoplov, "[Handling throws/throw idiom](https://gist.github.com/trashgenerator/d58e05522d2f83709e1a601564b68fee)", September 2018

- Gokan EKINCI, "[try-with-resources](https://gist.github.com/eau-de-la-seine/9e2e74d6369aef4a76aa50976e34de6d)", December 2018

## Other possibilities

- Alex Hornbake, "[refuse. conditional return keyword](https://gist.github.com/alexhornbake/6a4c1c6a0f2a063da6dda1bf6ec0f5f3)", June 2019

- yaxinlx, "[Use ? as suffix to remove the last error value from multi-value tuples](https://gist.github.com/yaxinlx/1e013fec0e3c2469f97074dbf5d2e2c0)", March 2019

- Plamen Stoev, "[Go 2 block-level checks](https://gist.github.com/coquebg/afe44e410f883a313dc849da3e1ff34c)", November 2018

- Peter Goetz, "[Formalize and Enforce Error Handling](https://medium.com/@peter.gtz/thinking-about-new-ways-of-error-handling-in-go-2-e56d116952f1)", September 2017

 - Fedir RYKHTIK, "[Go 2 error handling with exclamation mark](https://gist.github.com/fedir/50158bc351b43378b829948290102470)", September 2018

 - Einthusan Vigneswaran, “[Error Aware Keywords - return, defer, if, != and forcing the error object to be the last argument](https://gist.github.com/einthusan/24e18f6359a31b3537815284cde0f6de)”, September 2018

- Andrew Phillips, “[Improving Go Error Handling](http://devmethodologies.blogspot.com/2017/10/improving-go-error-handling.html)”, October 2017


# Uncategorized

Please help categorize the rest of the proposals here.

- Joe Lapp, "[`on...return` for error handling](https://github.com/golang/go/issues/48855)", Oct 2021

- Andrew Gwozdziewycz, "[Check for Go Errors](http://sigusr2.net/check-for-go-errors.html)", June 2019 

- DeedleFake, "[Feedback for Go 2 Design Drafts](https://deedlefake.com/2018/08/feedback-for-go-2-design-drafts/)", August 2018

- Loki Verloren, “[Go 2 error handling feedback and my thoughts on how to improve programmer's efficiency and experience](https://gist.github.com/l0k1verloren/8aec03b8c48fdb5d3dab3a77153ce162)”, September 2018

- Gima, "[Procedural code, separate error handling](https://gitlab.com/snippets/1726097)", June 2018

- Konstantin, "[error handling for error-tree](https://github.com/Konstantin8105/Go2ErrorTree)", [Discyssion](https://github.com/golang/go/issues/32099) May 2019

## Adding your feedback

Please format all entries as below.

- _Your Name_, “[_Title_](#URL)”, _month year_

To make it easier to see new feedback, please add your new proposal to the top of the section it is placed in.