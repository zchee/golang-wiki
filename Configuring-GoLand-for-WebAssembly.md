## Configuring GoLand for WebAssembly (Wasm) projects

When you first open or start a WebAssembly project in GoLand, it won't understand the "*syscall/js*" package.

That's easily fixable, by changing the **GOOS** and **GOARCH** values in the project settings, as per the screenshots below.

![Goland Wasm Setup pic1](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup1.png)

![Goland Wasm Setup pic2](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup2.png)

![Goland Wasm Setup pic3](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup3.png)

![Goland Wasm Setup pic4](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup4.png)