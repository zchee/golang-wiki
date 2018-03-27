[`go generate`](https://blog.golang.org/generate) is only useful if you have tools to use it with! Here is an incomplete list of useful tools that generate code.

* [goyacc](https://godoc.org/golang.org/x/tools/cmd/goyacc) – Yacc for Go.
* [stringer](https://godoc.org/golang.org/x/tools/cmd/stringer) – Implements `fmt.Stringer` interface for enums.
* [gostringer](https://godoc.org/github.com/sourcegraph/gostringer) – Implements `fmt.GoStringer` interface for enums.
* [jsonenums](https://github.com/campoy/jsonenums) – Implements `json.Marshaler` and `json.Unmarshaler` interfaces for enums.
* [gojson](https://github.com/ChimeraCoder/gojson) - Generates go struct definitions from example json documents.
* [vfsgen](https://github.com/shurcooL/vfsgen) - Generates a vfsdata.go file that statically implements the given virtual filesystem.
* [goreuse](https://github.com/dc0d/goreuse) - Generates Go code using a package as a generic template by replacing definitions.
* [embedfiles](https://4d63.com/embedfiles) - Embeds files into Go code.
* [ragel](https://www.colm.net/open-source/ragel/) - State machine compiler
* [peachpy](https://github.com/Maratyszcza/PeachPy) - x86-64 assembler embedded in Python, generates Go assembly
* [bundle](https://godoc.org/golang.org/x/tools/cmd/bundle) - Bundle creates a single-source-file version of a source package suitable for inclusion in a particular target package.
* [msgp](https://github.com/tinylib/msgp) - A Go code generator for MessagePack
* [protobuf](https://github.com/golang/protobuf) - protobuf
* [thriftrw](https://github.com/thriftrw/thriftrw-go) - thrift
* [gogen-avro](https://github.com/actgardner/gogen-avro) - avro
* [swagger-gen-types](https://github.com/dnephin/swagger-gen-types) - go types from swagger specifications