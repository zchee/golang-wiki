Go 1.11 adds an experimental port to WebAssembly.

WebAssembly is described on its [home page](https://webassembly.org) as:

> WebAssembly (abbreviated _Wasm_) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable target for compilation of high-level languages like C/C++/Rust, enabling deployment on the web for client and server applications.

This page will be updated over time with more information relevant to Go's support for WebAssembly.

# Example

To compile a basic Go package for the web:

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, WebAssembly!")
}
```

Run:

```sh
$ GOOS=js GOARCH=wasm go build -o main.wasm
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

And copy over the JavaScript support file:

```sh
$ cp $(go env GOROOT)/misc/wasm/wasm_exec.js .
```

Then serve those three files (`index.html`, `wasm_exec.js`, and `main.wasm`) to a web browser. For example, with [`goexec`](https://github.com/shurcooL/goexec#goexec):

```sh
$ goexec 'http.ListenAndServe(":8080", http.FileServer(http.Dir(".")))'
```

(Or use your own [basic HTTP server command](https://play.golang.org/p/pZ1f5pICVbV).)

Finally, navigate to http://localhost:8080/index.html, open the JavaScript debug console, and you should see the output. You can modify the program, rebuild `main.wasm`, and refresh to see new output.

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

# Editor configuration

* [Configuring GoLand for WebAssembly](https://github.com/golang/go/wiki/Configuring-GoLand-for-WebAssembly) - Shows the exact steps needed for getting Wasm working in GoLand