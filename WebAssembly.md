Go 1.11 adds an experimental port to WebAssembly.

WebAssembly is described on its [home page](https://webassembly.org) as:

> WebAssembly (abbreviated _Wasm_) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable target for compilation of high-level languages like C/C++/Rust, enabling deployment on the web for client and server applications.

This page will be updated over time with more information relevant to Go's support for WebAssembly.

**NOTE:** if you ever set the `GOROOT` environment variable to the path of an earlier Go SDK version other than the version of the `go` command, please unset this environment variable to avoid problems in the following tutorial.

# Example

To compile a basic Go package for the web:

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, WebAssembly!")
}
```

Set `GOOS=js` and `GOARCH=wasm` environment variables to compile for WebAssembly:

```sh
$ GOOS=js GOARCH=wasm go build -o main.wasm
```

That will build the package and produce an executable WebAssembly module file main.wasm. The .wasm file extension will make it easier to serve it over HTTP with the correct Content-Type header later on. To execute main.wasm in a browser, we'll also need a JavaScript support file and an HTML page that connects everything together.

Copy the JavaScript support file:

```sh
$ cp "$(go env GOROOT)/misc/wasm/wasm_exec.js" .
```

Create an `index.html` file:

```HTML
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="wasm_exec.js"></script>
		<script>
			const go = new Go();
			WebAssembly.instantiateStreaming(fetch("main.wasm"), go.importObject).then((result) => {
				go.run(result.instance);
			});
		</script>
	</head>
	<body></body>
</html>
```

(If your browser doesn't yet support `WebAssembly.instantiateStreaming`, you can use a [polyfill](https://github.com/golang/go/blob/b2fcfc1a50fbd46556f7075f7f1fbf600b5c9e5d/misc/wasm/wasm_exec.html#L17-L22).)

Then serve those three files (`index.html`, `wasm_exec.js`, and `main.wasm`) to a web browser. For example, with [`goexec`](https://github.com/shurcooL/goexec#goexec):

```sh
$ goexec 'http.ListenAndServe(":8080", http.FileServer(http.Dir(".")))'
```

(Or use your own [basic HTTP server command](https://play.golang.org/p/pZ1f5pICVbV).)

Finally, navigate to http://localhost:8080/index.html, open the JavaScript debug console, and you should see the output. You can modify the program, rebuild `main.wasm`, and refresh to see new output.

## Executing WebAssembly with Node.js (for go run, go test)

It's possible to execute compiled WebAssembly modules using Node.js rather than a browser. The `go_js_wasm_exec` script in `misc/wasm` directory of the Go installation can be used with [`-exec` flag](https://golang.org/cmd/go/#hdr-Compile_and_run_Go_program) of the `go` command.

Install `node` and make sure it's in your `PATH`. Set `-exec` flag to the location of `go_js_wasm_exec`:

```
$ GOOS=js GOARCH=wasm go run -exec="$(go env GOROOT)/misc/wasm/go_js_wasm_exec" .
Hello, WebAssembly!
$ GOOS=js GOARCH=wasm go test -exec="$(go env GOROOT)/misc/wasm/go_js_wasm_exec"
PASS
ok  	example.org/my/pkg	0.800s
```

Adding `go_js_wasm_exec` to your `PATH` will allow `go run` and `go test` to work for `js/wasm` without having to manually provide the `-exec` flag each time:

```
$ export PATH="$PATH:$(go env GOROOT)/misc/wasm"
$ GOOS=js GOARCH=wasm go run .
Hello, WebAssembly!
$ GOOS=js GOARCH=wasm go test
PASS
ok  	example.org/my/pkg	0.800s
```

# Interacting with the DOM

See https://godoc.org/syscall/js.

# Debugging

WebAssembly doesn't *yet* have any support for debuggers, so you'll need to use the good 'ol `println()` approach for now to display output on the JavaScript console.

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
    * Uses the 2d canvas, and a 2d physics engine.  Click around on the screen to create objects then watch as gravity takes hold!
  * [splashy](https://stdiopt.github.io/gowasm-experiments/splashy)
    * Used the webgl canvas.  Click around on the screen to generate paint...
  * [arty](https://stdiopt.github.io/gowasm-experiments/arty/client) (**NEW**)
* [Drawing simple 3D objects on the 2D canvas](https://justinclift.github.io/wasmGraph1/) ([source code](https://github.com/justinclift/wasmGraph1/))
  * Displays wireframe solids on the 2d canvas, using basic matrix maths.  Use wasd/keypad keys to rotate.
* [Gomeboycolor-wasm](https://github.com/djhworld/gomeboycolor-wasm) - WASM port of an experimental Gameboy Color emulator.  The [matching blog post](https://djhworld.github.io/post/2018/09/21/i-ported-my-gameboy-color-emulator-to-webassembly/) contains some interesting technical insights.

# Editor configuration

* [Configuring GoLand for WebAssembly](https://github.com/golang/go/wiki/Configuring-GoLand-for-WebAssembly) - Shows the exact steps needed for getting Wasm working in GoLand