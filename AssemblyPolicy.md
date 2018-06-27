# Assembly Policy

This document describes when and how to add assembly code to routines in the Go-maintained packages. This document is a work in progress.

In general, the rules are:

* we prefer portable Go, not assembly. Code in assembly means (N packages * M architectures) to maintain, rather than just N packages.

* assembly code needs benchmarks showing it's worth it

* minimize use of assembly. We'd rather have a small amount of assembly for a 50% speedup rather than twice as much assembly for a 55% speedup. Explain the decision to place the assembly/Go boundary where it is.

* explain why you need the assembly. What changes in the compiler and standard library would allow you to replace this assembly with Go? (New intrinsics, SSA pattern matching, other optimizations.)

* make your assembly easy to review, and ideally auto-generated from a Go program so we can review the generator program. Comment it well.

* test it well. The bar for new assembly code is high. It needs commensurate test coverage. The generic existing high-level tests are often not enough to test hundreds of lines of assembly. Test subroutines individually. Fuzz it against the Go implementation.

## Future directions

* if possible, port existing reviewed implementations. A tool should make it easy to review diffs from decompiler output. Consider the license implications.
