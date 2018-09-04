Go 1.11 adds an experimental port to WebAssembly.

WebAssembly is described on its [home page](https://webassembly.org) as:

> WebAssembly (abbreviated _Wasm_) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable target for compilation of high-level languages like C/C++/Rust, enabling deployment on the web for client and server applications.

This page will be updated over time with more information relevant to Go's support for WebAssembly.

# Prerequisite 

Note, if you ever set the `GOROOT` environment variable to an old Go SDK path, please remove this environment variable. This environment variable is not needed any more. Otherwise, the `go build` command below will report error: 

```
go tool compile: exit status 2
compile: unknown architecture "wasm"
```

# Example

To compile the basic Go program for the web:

```go
package main

func main() {
	println("Hello, WebAssembly!")
}
```

Run:

```sh
$ GOARCH=wasm GOOS=js go build -o test.wasm main.go
```

And copy over the HTML & JS support files:

```sh
$ cp $(go env GOROOT)/misc/wasm/wasm_exec.{html,js} .
```

Then serve those three files (`wasm_exec.html`, `wasm_exec.js`, and `test.wasm`) to a web browser.

For a basic HTTP server:

```go
package main

import (
	"flag"
	"log"
	"net/http"
	"strings"
)

var (
	listen = flag.String("listen", ":8080", "listen address")
	dir    = flag.String("dir", ".", "directory to serve")
)

func main() {
	flag.Parse()
	log.Printf("listening on %q...", *listen)
	log.Fatal(http.ListenAndServe(*listen, http.HandlerFunc(func(resp http.ResponseWriter, req *http.Request) {
		if strings.HasSuffix(req.URL.Path, ".wasm") {
			resp.Header().Set("content-type", "application/wasm")
		}

		http.FileServer(http.Dir(*dir)).ServeHTTP(resp, req)
	})))
}
```

Now navigate to http://localhost:8080/wasm_exec.html, click "Run", and you should see the output in the JavaScript debug console.

# Interacting with the DOM

See https://tip.golang.org/pkg/syscall/js/

# Debugging

WebAssembly doesn't *yet* have any support for debuggers, so you'll need to use the good 'ol `println()` approach for now.

An official [WebAssembly Debugging Subgroup](https://github.com/WebAssembly/debugging) has been created to address this, with some initial investigation and proposals under way:

* [WebAssembly Debugging Capabilities Living Standard](https://fitzgen.github.io/wasm-debugging-capabilities/) ([source code for the doc](https://github.com/fitzgen/wasm-debugging-capabilities))
* [DWARF for WebAssembly Target](https://yurydelendik.github.io/webassembly-dwarf/) ([source code for the doc](https://github.com/yurydelendik/webassembly-dwarf/))

Please get involved and help drive this if you're interested in the Debugger side of things. :smile:

# Tutorials + Articles

* [Building a Calculator with Go and WebAssembly](https://youtu.be/4kBvvk2Bzis)
([Source code](https://blog.owulveryck.info/2018/06/08/some-notes-about-the-upcoming-webassembly-support-in-go.html))
* [Get Going with WebAssembly](https://www.youtube.com/watch?v=iTrx0BbUXI4)

# Further reference examples

* [GoWasm Experiments](https://github.com/stdiopt/gowasm-experiments) - Demonstrates working code for several common call types
  * [bouncy](https://stdiopt.github.io/gowasm-experiments/bouncy)
  * [rainbow-mouse](https://stdiopt.github.io/gowasm-experiments/rainbow-mouse)
  * [repulsion](https://stdiopt.github.io/gowasm-experiments/repulsion)
  * [bumpy](https://stdiopt.github.io/gowasm-experiments/bumpy)
  * [splashy](https://stdiopt.github.io/gowasm-experiments/splashy)
  * [arty](https://stdiopt.github.io/gowasm-experiments/arty/client) (**NEW**)
* [Drawing simple 3D objects on the 2D canvas](https://justinclift.github.io/wasmGraph1/) ([source code](https://github.com/justinclift/wasmGraph1/))
  * Displays wireframe solids on the 2d canvas, using basic matrix maths.  Use wasd/keypad keys to rotate.

# Editor configuration

* [Configuring GoLand for WebAssembly](https://github.com/golang/go/wiki/Configuring-GoLand-for-WebAssembly) - Shows the exact steps needed for getting Wasm working in GoLand