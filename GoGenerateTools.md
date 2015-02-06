[`go generate`](https://blog.golang.org/generate) is only useful if you have tools to use it with! Here is an incomplete list of useful tools that generate code.

* [go tool yacc](https://golang.org/cmd/yacc/) – Yacc for Go.
* [stringer](https://godoc.org/golang.org/x/tools/cmd/stringer) – Implements `fmt.Stringer` interface for enums.
* [gostringer](https://godoc.org/github.com/sourcegraph/gostringer) – Implements `fmt.GoStringer` interface for enums.
* [jsonenums](https://github.com/campoy/jsonenums) – Implements `json.Marshaler` and `json.Unmarshaler` interfaces for enums.
* [gen-mocks](https://sourcegraph.com/sourcegraph/gen-mocks) – Generate mocks for interfaces. Used in [go-sourcegraph](https://sourcegraph.com/sourcegraph.com/sourcegraph/go-sourcegraph@master/.tree/sourcegraph).