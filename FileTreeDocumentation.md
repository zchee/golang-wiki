# Go project directory layout

The Go project itself contains a number of subdirectories. This document will provide a brief overview, but many of these directories have individual README.md or README files that describe their purpose in detail. 

- [api](#api)
- [bin](#bin)
- [blog](#blog)
- [doc](#doc)
- [lib](#lib)
- [misc](#misc)
- [pkg](#pkg)
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

## pkg

## src

The `src` directory contains the source code for the standard library and, in `src/cmd`, tool chain.

## test

The `test` directory contains extensive additional tests for the runtime and tool chain.