# Assembly Policy

This document describes when and how to add assembly code to routines in the Go-maintained packages. This document is a work in progress.

In general, the rules are:

* We prefer portable Go, not assembly. Code in assembly means (N packages * M architectures) to maintain, rather than just N packages.

* Minimize use of assembly. We'd rather have a small amount of assembly for a 50% speedup rather than twice as much assembly for a 55% speedup. Explain the decision to place the assembly/Go boundary where it is in the commit message, and support it with benchmarks.

* Explain the root causes in code comments or commit messages. What changes in the compiler and standard library would allow you to replace this assembly with Go? (New intrinsics, SSA pattern matching, other optimizations.)

* Make your assembly easy to review; ideally, auto-generate it using a simpler Go program. Comment it well.

* Test it well. The bar for new assembly code is high; it needs commensurate test coverage. Existing high-level tests for Go implementations are often inadequate for hundreds of lines of assembly. Test subroutines individually. Fuzz the assembly implementation against the Go implementation.

## Future directions

* If possible, port existing reviewed implementations. A tool should make it easy to review diffs from decompiler output. Consider the license implications.
