An overview of tools that will help improve your Go code

## All-in-one

  - [golangci-lint](https://github.com/golangci/golangci-lint) - Bundle of `gofmt`, `golint`, `govet` and many other tools that shares work between the different linters for better performance. Recommended by the original author to replace gometalinter (Drop-in replacement).
  - DEPRECATED: [gometalinter](https://github.com/alecthomas/gometalinter) - Automates the installation, configuration and application of `gofmt`, `golint`, `govet` and several other code validation tools.

## Code Formatting

### Articles

  - [Formatting Go Code with gofmt](http://golangtutorials.blogspot.com/2011/06/formatting-go-code-with-gofmt.html)

### Tools

  - [air](https://github.com/cosmtrek/air) - Live reload for Go apps
  - [gofmt](https://pkg.go.dev/cmd/gofmt/) - Start with the standard Go code formatter.
  - [golint](https://github.com/golang/lint) - Detects style mistakes in Go code.
  - [goimports](https://pkg.go.dev/golang.org/x/tools/cmd/goimports) - Format code and fix your import statements.
  - [gofumpt](https://github.com/mvdan/gofumpt) - A stricter gofmt.
  - [revive](https://github.com/mgechev/revive) - Fast, configurable, extensible, flexible, and beautiful linter for Go.

## Code generation, Templating and Generics

  - [json-to-go](https://mholt.github.io/json-to-go/) - Generate Go structs from JSON.
  - [Go gen](http://clipperhouse.github.io/gen/) - Type-driven code generation (generics)
  - [gojson](https://github.com/ChimeraCoder/gojson) - Another Go struct generator.
  - [gotemplate](https://github.com/ncw/gotemplate) - Package-based templating system for Go.
  - [sqlgen](https://github.com/drone/sqlgen) - Generate Go code for SQL interactions.
  - [zek](https://github.com/miku/zek) - Generate Go struct from XML.
  - [apidocgen](https://github.com/alovn/apidocgen) - Generate web apis markdown docs and mocks.

## Refactoring

### Articles

  - [gorename - easy refactoring](https://texlution.com/post/gorename/)
  - [Refactoring Tools](http://blog.ralch.com/tutorial/golang-tools-refactoring/) - An overview of refactoring tools for Go.
  - [Quick renaming with gofmt](http://technosophos.com/2015/09/26/quick-go-hack-renaming-structs.html)

### Tools

- [eg](https://pkg.go.dev/golang.org/x/tools/cmd/eg) - Example-based refactoring tool for Go.
- [gofmt](https://pkg.go.dev/cmd/gofmt/) - Start with the standard Go code formatter.
- [gorename](https://golang.org/x/tools/refactor/rename) - Renaming tool for Go.

## Error Detection

### Articles

  - [Go Inspection Tools](https://blog.ralch.com/articles/golang-tools-inspection/) - An overview of tools for Go code inspection.

### Tools

  - [AlignCheck, StructCheck, VarCheck](https://github.com/opennota/check/) - A suite of tools for checking your code.
  - [errcheck](https://github.com/kisielk/errcheck) - Ensure you check your error conditions.
  - [go vet](https://pkg.go.dev/cmd/vet/) - Read this first on how to use the `go vet` command.
  - [SafeSQL](https://github.com/stripe/safesql) - Protect against unsafe SQL in your code.

## Navigation

  - [Go Guru - User Manual](https://go.dev/s/using-guru) - A tool for understanding Go code.
  - [Pythia](https://github.com/fzipp/pythia) - A browser-based UI for Go Guru.

## Visualization

  - [godepgraph](http://github.com/kisielk/godepgraph) - A tool for generating dependency graphs of Go code.
