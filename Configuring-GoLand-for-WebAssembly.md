### [← Back](https://github.com/golang/go/wiki/WebAssembly) to the main WebAssembly page.

# Configuring GoLand for WebAssembly (Wasm) projects

## Initial project configuration

When you first open or start a WebAssembly project in GoLand, it won't understand the "*syscall/js*" package.

That's easily fixable, by changing the **GOOS** and **GOARCH** values in the project settings, as per the screenshots below.

![GoLand Wasm Setup pic1](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup1.png)

**Note** - The screenshot below shows how to access **Settings** on a Linux desktop.  If you're using macOS, you'll probably need to access them through the standard macOS **Preferences** option.
![GoLand Wasm Setup pic2](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup2.png)

![GoLand Wasm Setup pic3](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup3.png)

![GoLand Wasm Setup pic4](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Setup4.png)


## Configuring Run/Debug settings

With the initial project settings changed, you'll probably want to configure the Run/Debug settings next.

That will let you recompile the .wasm file by just launching `Run` (<kbd>Shift</kbd>+<kbd>F10</kbd> on Linux).

![GoLand Wasm Build pic2](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build2.png)

![GoLand Wasm Build pic3](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build3.png)

![GoLand Wasm Build pic4](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build4.png)

![GoLand Wasm Build pic5](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build5.png)

![GoLand Wasm Build pic6](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build6.png)

![GoLand Wasm Build pic7](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build7.png)

![GoLand Wasm Build pic8](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build8.png)

![GoLand Wasm Build pic9](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build9.png)

![GoLand Wasm Build pic10](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build10.png)

![GoLand Wasm Build pic11](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build11.png)

![GoLand Wasm Build pic12](https://github.com/justinclift/wasmWikiPics/raw/master/png/Golang-Wasm-Build12.png)

Finished, your GoLand setup should now be complete.

### [← Back](https://github.com/golang/go/wiki/WebAssembly) to the main WebAssembly page.