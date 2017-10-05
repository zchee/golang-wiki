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

### misc/chrome

### misc/git

### misc/ios

### misc/linkcheck

### misc/nacl

### misc/sortac

### misc/swig

### misc/tour

### misc/trace

## pkg

### pkg/include

### pkg/obj

### pkg/tool

## src

The `src` directory contains the source code for the standard library and, in `src/cmd`, tool chain.

## test

The `test` directory contains extensive additional tests for the runtime and tool chain.