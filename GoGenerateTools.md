[`go generate`](https://blog.golang.org/generate) is only useful if you have tools to use it with! Here is an incomplete list of useful tools that generate code.

* [go tool yacc](https://golang.org/cmd/yacc/) – Yacc for Go.
* [stringer](https://godoc.org/golang.org/x/tools/cmd/stringer) – Implements `fmt.Stringer` interface for enums.
* [gostringer](https://godoc.org/github.com/sourcegraph/gostringer) – Implements `fmt.GoStringer` interface for enums.
* [jsonenums](https://github.com/campoy/jsonenums) – Implements `json.Marshaler` and `json.Unmarshaler` interfaces for enums.
* [gojson](https://github.com/ChimeraCoder/gojson) - Generates go struct definitions from example json documents.
* [vfsgen](https://github.com/shurcooL/vfsgen) - Generates a vfsdata.go file that statically implements the given virtual filesystem.
