# Introduction

If you reached this page because you saw an error message like the following printed by a Go program running on macOS 12 Monterey:
```
fatal error: runtime: bsdthread_register error

runtime stack:
runtime.throw(0x20594e0, 0x21)
	/usr/local/go/src/runtime/panic.go:619 +0x81 fp=0x7ff7bfeff878 sp=0x7ff7bfeff858 pc=0x1029751
runtime.goenvs()
	/usr/local/go/src/runtime/os_darwin.go:129 +0x83 fp=0x7ff7bfeff8a8 sp=0x7ff7bfeff878 pc=0x10272d3
runtime.schedinit()
	/usr/local/go/src/runtime/proc.go:496 +0xa4 fp=0x7ff7bfeff900 sp=0x7ff7bfeff8a8 pc=0x102c014
runtime.rt0_go(0x7ff7bfeff930, 0x3, 0x7ff7bfeff930, 0x1000000, 0x3, 0x7ff7bfeffab0, 0x7ff7bfeffabf, 0x7ff7bfeffac3, 0x0, 0x7ff7bfeffacc, ...)
	/usr/local/go/src/runtime/asm_amd64.s:252 +0x1f4 fp=0x7ff7bfeff908 sp=0x7ff7bfeff900 pc=0x1052c64
```
then you are running a program built with an old version of Go (Go 1.10 or before). You will need to update your program or rebuild it with a newer version of Go.

# Details

Programs built with Go 1.10 or before use a way of issuing system calls that is no longer supported by the kernel on macOS 12 Monterey. In [Go 1.11](https://go.dev/doc/go1.11#runtime) and later, system calls are issued via `libSystem.dylib`, which is supported by the OS.

# What to do

If this is a program you downloaded or installed (for example, using Homebrew), you will need to download or install a newer version of it that is built with a newer version of Go.

If this is a program you built from source, you will need to rebuild it with a newer version of Go.

You might want to check your $PATH and manually clean up `$GOPATH/bin` and other old relevant Go binaries you've installed.

If you're trying to compile Go, `go tool dist clean` might help.