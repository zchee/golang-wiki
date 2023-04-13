<!-- STOP.  PRESS THE BACK BUTTON.  DO NOT EDIT.  DO NOT CLICK "SAVE PAGE". -->
<!-- If you have a question, see https://go.dev/wiki/Questions -->
<!-- This is a wiki. We trust you to be a good person. -->
<!-- 
Google Online Security Blog
The latest news and insights from Google on security and safety on the Internet

January 12, 2023
Supporting the Use of Rust in the Chromium Project
Posted by Dana Jansens (she/her), Chrome Security Team
We are pleased to announce that moving forward, the Chromium project is going to support the use of third-party Rust libraries from C++ in Chromium. To do so, we are now actively pursuing adding a production Rust toolchain to our build system. This will enable us to include Rust code in the Chrome binary within the next year. We’re starting slow and setting clear expectations on what libraries we will consider once we’re ready.

In this blog post, we will discuss how we arrived at the decision to support third-party Rust libraries at this time, and not broader usage of Rust in Chromium.

Why We Chose to Bring Rust into Chromium

Our goal in bringing Rust into Chromium is to provide a simpler (no IPC) and safer (less complex C++ overall, no memory safety bugs in a sandbox either) way to satisfy the rule of two, in order to speed up development (less code to write, less design docs, less security review) and improve the security (increasing the number of lines of code without memory safety bugs, decreasing the bug density of code) of Chrome. And we believe that we can use third-party Rust libraries to work toward this goal.

Rust was developed by Mozilla specifically for use in writing a browser, so it’s very fitting that Chromium would finally begin to rely on this technology too. Thank you Mozilla for your huge contribution to the systems software industry. Rust has been an incredible proof that we should be able to expect a language to provide safety while also being performant.

We know that C++ and Rust can play together nicely, through tools like cxx, autocxx bindgen, cbindgen, diplomat, and (experimental) crubit. However there are also limitations. We can expect that the shape of these limitations will change in time through new or improved tools, but the decisions and descriptions here are based on the current state of technology.

How Chromium Will Support the Use of Rust

The Chrome Security team has been investing time into researching how we should approach using Rust alongside our C++ code. Understanding the implications of incrementally moving to writing Rust instead of C++, even in the middle of our software stack. What the limits of safe, simple, and reliable interop might be.

Based on our research, we landed on two outcomes for Chromium.

We will support interop in only a single direction, from C++ to Rust, for now. Chromium is written in C++, and the majority of stack frames are in C++ code, right from main() until exit(), which is why we chose this direction. By limiting interop to a single direction, we control the shape of the dependency tree. Rust can not depend on C++ so it cannot know about C++ types and functions, except through dependency injection. In this way, Rust can not land in arbitrary C++ code, only in functions passed through the API from C++.
We will only support third-party libraries for now. Third-party libraries are written as standalone components, they don’t hold implicit knowledge about the implementation of Chromium. This means they have APIs that are simpler and focused on their single task. Or, put another way, they typically have a narrow interface, without complex pointer graphs and shared ownership. We will be reviewing libraries that we bring in for C++ use to ensure they fit this expectation.
The Interop Between Rust and C++ in Chromium

We have observed that most successful C/C++ and Rust interop stories to date have been built around interop through narrow APIs (e.g. libraries for QUIC or bluetooth, Linux drivers) or through clearly isolated components (e.g. IDLs, IPCs). Chrome is built on foundational but really wide C++ APIs, such as the //content/public layer. We examined what it would mean for us to build Rust components against these types of APIs. At a high level what we found was that because C++ and Rust play by different rules, things can go sideways very easily.

For example, Rust guarantees temporal memory safety with static analysis that relies on two inputs: lifetimes (inferred or explicitly written) and exclusive mutability. The latter is incompatible with how the majority of Chromium’s C++ is written. We hold redundant mutable pointers throughout the system, and pointers that provide multiple paths to reach mutable pointers. We have cyclical mutable data structures. This is especially true in our browser process, which contains a giant interconnected system of (mutable) pointers. If these C++ pointers were also used as Rust references in a complex or long-lived way, it would require our C++ authors to understand the aliasing rules of Rust and prevent the possibility of violating them, such as by:

Returning the same mutable pointer from a function twice, where the first may still be held.
Passing overlapping pointers where one is mutable into Rust, in a way that they may be held as references at the same time.
Mutating state that is visible to Rust through a shared or mutable reference.
Without interop tools providing support via the compiler and the type system, developers would need to understand all of the assumptions being made by Rust compiler, in order to not violate them from C++. In this framing, C++ is much like unsafe Rust. And while unsafe Rust is very costly to a project, its cost is managed by keeping it encapsulated and to the minimum possible. In the same way, the full complexity of C++ would need to be encapsulated from safe Rust. Narrow APIs designed for interop can provide similar encapsulation, and we hope that interop tools can provide encapsulation in other ways that allow wider APIs between the languages.

The high-level summary is that without additional interop tooling support:

Passing pointers/references across languages is risky.
Narrow interfaces between the languages is critical to make it feasible to write code correctly.
Any cross-language interop between arbitrary code introduces difficulties where concepts in one language are not found in the other. For Rust calling into C++, support for language features like templates or inheritance can be difficult for a binding generator to support. For C++ calling into Rust, proc macros, and traits are examples that provide similar challenges. At times, the impedance mismatch represents intentional design choices made for either language, however they also imply limits on FFI (interop) between the languages. We rely on interop tools to model the ideas of each language in a way that makes sense to the other, or to disallow them.

Accessing the Rust Ecosystem from Chromium

These challenges present an opportunity, both to make interop easier and more seamless, but also to get access to a wider range of libraries from either language. Google is investing in Crubit, an experiment in how to increase the fidelity of interop between C++ and Rust and express or encapsulate the requirements of each language to the other.

The Rust ecosystem is incredibly important, especially to a security-focused open source project like Chromium. The ecosystem is enormous (96k+ crates on crates.io) and growing, with investment from the systems development industry at large, including Google. Chrome relies heavily on third-party code, and we need to keep up with where that third-party investment is happening. It is critical that we build out support for including Rust into the Chromium project.

We will be following this strategy to establish norms, and to maintain a level of API review through the third-party process, while we look to the future of interop support pushing the boundaries of what is possible and reasonable to do between Rust and C++.


Some Other Related Content

Memory unsafety is an industry-wide problem, and making use of Rust is one part of a strategy to move the needle in this area. Recently, Android and Apple have each published a great blog post on the subject if you’re interested in learning more. With Chrome’s millions of lines of C++, we’re still working hard to improve the safety of our C++ too, through projects such as MiraclePtr.

Edward Fernandez
Share
No comments:
Post a Comment
You are welcome to contribute comments, but they should be relevant to the conversation. We reserve the right to remove off-topic remarks in the interest of keeping the conversation focused and engaging. Shameless self-promotion is well, shameless, and will get canned.

Note: Only a member of this blog may post a comment.

‹
›
Home
View web version
Powered by Blogger.