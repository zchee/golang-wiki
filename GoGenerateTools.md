[`go generate`](https://go.dev/blog/generate) is only useful if you have tools to use it with! Here is an incomplete list of useful tools that generate code.

* [goyacc](https://pkg.go.dev/golang.org/x/tools/cmd/goyacc) – Yacc for Go.
* [stringer](https://pkg.go.dev/golang.org/x/tools/cmd/stringer) – Implements `fmt.Stringer` interface for enums.
* [gostringer](https://pkg.go.dev/github.com/sourcegraph/gostringer) – Implements `fmt.GoStringer` interface for enums.
* [jsonenums](https://github.com/campoy/jsonenums) – Implements `json.Marshaler` and `json.Unmarshaler` interfaces for enums.
* [go-syncmap](https://pkg.go.dev/github.com/searKing/golang/tools/cmd/go-syncmap) - Generates Go code using a package as a generic template for `sync.Map`.
* [go-syncpool](https://pkg.go.dev/github.com/searKing/golang/tools/cmd/go-syncpool) - Generates Go code using a package as a generic template for `sync.Pool`.
* [go-atomicvalue](https://pkg.go.dev/github.com/searKing/golang/tools/cmd/go-atomicvalue) - Generates Go code using a package as a generic template for `atomic.Value`.
* [go-nulljson](https://pkg.go.dev/github.com/searKing/golang/tools/cmd/go-nulljson) - Generates Go code using a package as a generic template that implements `database/sql.Scanner` and `database/sql/driver.Valuer`.
* [go-enum](https://pkg.go.dev/github.com/searKing/golang/tools/cmd/go-enum) - Generates Go code using a package as a generic template which implements interface `fmt.Stringer` | `binary` | `json` | `text` | `sql` | `yaml` for enums.
* [enumer](https://pkg.go.dev/github.com/alvaroloes/enumer) - Generates Go code that convert Go enum to/from strings.
* [go-import](https://pkg.go.dev/github.com/searKing/golang/tools/cmd/go-import) — Performs auto import of non go files.
* [gojson](https://github.com/ChimeraCoder/gojson) - Generates go struct definitions from example json documents.
* [vfsgen](https://github.com/shurcooL/vfsgen) - Generates a vfsdata.go file that statically implements the given virtual filesystem.
* [goreuse](https://github.com/dc0d/goreuse) - Generates Go code using a package as a generic template by replacing definitions.
* [embedfiles](https://4d63.com/embedfiles) - Embeds files into Go code.
* [ragel](https://www.colm.net/open-source/ragel/) - State machine compiler
* [peachpy](https://github.com/Maratyszcza/PeachPy) - x86-64 assembler embedded in Python, generates Go assembly
* [bundle](https://pkg.go.dev/golang.org/x/tools/cmd/bundle) - Bundle creates a single-source-file version of a source package suitable for inclusion in a particular target package.
* [msgp](https://github.com/tinylib/msgp) - A Go code generator for MessagePack
* [protobuf](https://github.com/golang/protobuf) - protobuf
* [thriftrw](https://github.com/thriftrw/thriftrw-go) - thrift
* [gogen-avro](https://github.com/actgardner/gogen-avro) - avro
* [swagger-gen-types](https://github.com/dnephin/swagger-gen-types) - go types from swagger specifications
* [avo](https://github.com/mmcloughlin/avo) - generate assembly code with Go
* [Wire](https://github.com/google/wire) - Compile-time Dependency Injection for Go
* [sumgen](https://github.com/smasher164/sumgen) - generate interface method implementations from sum-type declarations
* [interface-extractor](https://github.com/urandom/interface-extractor) - generates an interface of a desired type, with only methods used within the package.
* [deep-copy](https://github.com/globusdigital/deep-copy) - creates a deep copy method for the given types.
* [libfsm](https://github.com/katef/libfsm) - fsm toolkit supporting (among others) Go and Go-flavored amd64 assembly for matching regexps
* [re2c](https://re2c.org/index.html) - lexer generator for C, C++ and Go
* [re2dfa](https://gitlab.com/opennota/re2dfa) - Transform regular expressions into finite state machines and output Go source code
* [pigeon](https://github.com/mna/pigeon) - a PEG parser generator for Go


