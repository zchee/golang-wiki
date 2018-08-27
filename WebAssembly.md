Go 1.11 adds an experimental port to WebAssembly.

WebAssembly is described on its [home page](https://webassembly.org) as:

> WebAssembly (abbreviated _Wasm_) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable target for compilation of high-level languages like C/C++/Rust, enabling deployment on the web for client and server applications.

This page will be updated over time with more information relevant to Go's support for WebAssembly.

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

Now navigate to http://localhost:8080/, click "Run", and you should see the output in the JavaScript debug console.

# Interacting with the DOM

See https://tip.golang.org/pkg/syscall/js/

# Tutorials + Articles

[Building a Calculator with Go and WebAssembly](https://youtu.be/4kBvvk2Bzis)
[Get Going with WebAssembly](https://www.youtube.com/watch?v=iTrx0BbUXI4)