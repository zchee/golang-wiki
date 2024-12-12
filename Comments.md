---
title: Comments
---

Go supports C-style `/* */` block comments and C++-style `//` line
comments.
Line comments are the norm.

## Doc comments

Packages and exported names should have doc comments.
Doc comments follow certain conventions and support a simple
formatting syntax.
For more information see [Go Doc Comments](https://go.dev/doc/comment).

## Directives

Certain tools, including the [go tool](https://pkg.go.dev/cmd/go) and
the [compiler](https://pkg.go.dev/cmd/compile) support directives that
may appear in comments.
With a couple of exceptions that exist for compatibility, this comment
directives are line comments that start with `//go:`, with no space
between the `//` and the `go:`.

### go tool directives

#### //go:build

The [go tool](https://pkg.go/dev/cmd/go) supports [build
constraints](https://pkg.go.dev/cmd/go#hdr-Build_constraints).
These are `//go:build` directives that describe conditions under which
a file should be included in the package.

Sample uses of constraints are:
- `//go:build ignore` is a convention that will keep a file from being
  part of the build. This is often used for programs that generate
  source code.
- `//go:build linux` will only build a file when building for
  Linux. This may be used in general for any operating system or
  architecture.
- `//go:build cgo` will only build a file when cgo is supported.
- `//go:build purego` is a convention that will only build a file when
  using pure Go; that is, no cgo or assembler code.

Constraints may also be expressions:
- `//go:build amd64 || arm64` will build a file on either amd64 or
  arm64.

Constraints can set the language version to use when compiling a
file. For example, the constraint `//go:build go1.23` will only build
a file when using Go 1.23 or later, and will use Go 1.23 language
semantics when building the file. This is convenient if go.mod is an
earlier version. For example, this could permit defining functions
that provide Go 1.23 [function
iterators](https://go.dev/blog/range-functions), but only when
building with Go 1.23 or later.

In Go 1.16 and earlier build constraints were written using comments
that started with `// +build`, and did not permit general expressions.
The [gofmt program](https://pkg.go.dev/cmd/gofmt) will rewrite the
older `// +build` syntax into the newer `//go:build` syntax.

#### //go:generate

The [go
generate](https://pkg.go.dev/cmd/go#hdr-Generate_Go_files_by_processing_source)
command looks for `//go:generate` directives to find commands to run.

An example of this directive would be `//go:generate stringer
-type=Enum` to run the [stringer
tool](https://pkg.go.dev/golang.org/x/tools/cmd/stringer) to define a
`String` method for values of an integer type.

#### //go:embed

The [embed package](https://pkg.go.dev/embed) uses `//go:embed`
directives to embed source files into the generated binary. A single
file may be embedded as a `string` or `[]byte`. A group of files may
be embedded as a `embed.FS`, which implements the [`fs.FS`
interface](https://pkg.go.dev/io/fs#FS).

For example, the contents of a subdirectory named templates can be
embedded into the program using a directive like:

```go
//go:embed templates
var templatesSource embed.FS

// tmpls holds the parsed embedded templates.
// This does not read files at run time,
// it parses the data embedded in the binary.
var tmpls = template.ParseFS(templatesSource)
```

### compiler directives

The Go compiler supports [several
directives](https://pkg.go.dev/cmd/compile#hdr-Compiler_Directives).

#### //line

The `//line` directive permits setting the file name and line and
column number to use for the following code.
For historicaly reasons this directive does not start with `//go:`.
This is useful when the Go file is generated from some other source,
and it's useful for error messages or stack tracebacks to refer to
that other source file rather than the generated source file.

Within a line, a `/*line` block comment may be used, which can be
helpful to set a column position.

```go
//line foo.src:10
var x = /*line foo.src:20:5*/ 3
```

#### //go:noescape

The `//go:noescape` directive must be followed by a function
declaration with no function body, indicating a function that is not
implemented in Go. The directive tells the compiler that pointers
passed to the function do not escape to the heap and are not returned
by the function.

#### Other compiler directives

There are a number of other compiler directives that serve special
purposes. For details the [compiler
documentation](https://pkg.go.dev/cmd/compile#hdr-Compiler_Directives).

- `//go:linkname`
- `//go:noinline`
- `//go:norace`
- `//go:nosplit`
- `//go:uintptrescapes`
- `//go:wasmimport`

#### Undocumented compiler directives

The compiler also supports some undocumented directives.
In general these should not be used in user code.
Some of these are only available when compiling the runtime package.

- `//go:nocheckptr`
- `//go:nointerface`
- `//go:nowritebarrier`
- `//go:nowritebarrierrec`
- `//go:registerparams`
- `//go:systemstack`
- `//go:uintptrkeepalive`
- `//go:yeswritebarrierrec`

### cgo comments

The [cgo tool](https://pkg.go.dev/cmd/cgo) uses a sequence of one or
more comments that appear immediately before a `import "C"` statement.
This sequence of comments, known as the cgo preamble, define names
that the Go code may refer to using the special `C` package.

```go
package main

// #include <stdio.h>
import "C"

func main() {
	C.puts(C.CString("hello world"))
}
```

Within the preamble, cgo recognizes directives that start with `#cgo`.
These may be used to set the C compiler and linker flags to use, or to
describe the behavior of some C functions.
For full details see the [cgo
documentation](https://pkg.go.dev/cmd/cgo).

#### cgo compiler directives

The cgo tool generates Go code, and that generated code uses some
special directives that are mostly only available in cgo-generated
code.
These are largely undocumented except in the cgo source code.

- `//go:cgo_dynamic_linker`
- `//go:cgo_export_dynamic`
- `//go:cgo_export_static`
- `//go:cgo_import_dynamic`
- `//go:cgo_import_static`
- `//go:cgo_ldflag`
- `//go:cgo_unsafe_args`
