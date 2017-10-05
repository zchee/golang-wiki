# Go project directory layout

The Go project itself contains a number of subdirectories. This document will provide a brief overview, but many of these directories have individual README.md or README files that describe their purpose in detail. 

- [api](#api)
- [bin](#bin)
- [blog](#blog)
- [doc](#doc)
- [lib](#lib)
- [misc](#misc)
    - [android](#miscandroid)
    - [arm](#miscarm)
    - [cgo](#misccgo)
    - [chrome](#miscchrome)
    - [git](#miscgit)
    - [ios](#miscios)
    - [linkcheck](#misclinkcheck)
    - [nacl](#miscnacl)
    - [sortac](#miscsortac)
    - [swig](#miscswig)
    - [tour](#misctour)
    - [trace](#misctrace)
- [pkg](#pkg)
    - [include](#pkginclude)
    - [obj](#pkgobj)
    - [tool](#pkgtool)
- [src](#src)
- [test](#test)

## api

The `api` directory contains machine checkable specifications for the Go standard library, to help enforce the [Go 1 compatibility promise](https://golang.org/doc/go1compat).

## bin

The `bin` directory contains the binaries of the project: `go`, `godoc`, and `gofmt`.

## blog

The `blog` directory contains the source and templates for [the Go blog](https://blog.golang.org/). However, the code for serving the blog is at https://godoc.org/golang.org/x/blog

## doc

The `doc` directory contains the resources served at https://golang.org/doc/

## lib

The `lib` directory contains a single subdirectory `lib/time` which contains a copy of the time zone database that Go uses if it cannot find the operating systems copy.

## misc

### misc/android

### misc/arm

### misc/cgo

The `misc/cgo` directory contains tests and examples of cgo.

### misc/chrome

The `misc/chrome` directory contains a Chrome extension for Go contributors.

### misc/git

The `misc/git` directory contains a pre-commit hook to ensure that go files have been run through gofmt.

### misc/ios

### misc/linkcheck

The `misc/linkcheck` directory contains a program for ensuring there are no missing links in the godoc website.

### misc/nacl

The `misc/nacl` directory contains Go's integration with nacl, which is used by [the Go playground](https://play.golang.org).

### misc/sortac

The `misc/sortac` directory contains a utility for sorting the `AUTHORS` and `CONTRIBUTORS` files.

### misc/swig

The `misc/swig` directory contains examples of using Go with [SWIG](https://github.com/swig/swig).

### misc/tour

The `misc/tour` directory contains the resources and source code for the [Go tour](https://tour.golang.org).

### misc/trace

The `misc/trace` directory contains a generated file used by `go tool trace`.

## pkg

The `pkg` directory contains platform-specific build artifacts. It will always contain the following:

### pkg/include

### pkg/obj

### pkg/tool

The `pkg/tool` directory contains the platform-specific tool chain exposed by the `go tool` command.

## src

The `src` directory contains the source code for the standard library and, in `src/cmd`, tool chain.

## test

The `test` directory contains extensive additional tests for the runtime and tool chain.