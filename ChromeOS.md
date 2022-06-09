# Introduction

You don't need to compile from source in Developer mode, you can just use the [Chromebrew](https://github.com/skycocker/chromebrew)-provided version.

If your Chromebook is relatively new, you can enable the Linux VM now built into ChromeOS to install Go without developer mode. Follow the steps from the following Google Support article to enable this feature- https://support.google.com/chromebook/answer/9145439. This has been tested on a Samsung Chromebook Plus on version 71.0.3578.127. If this feature is not available for you, you will need to enable Developer Mode.

This tutorial will show you how to install, build, and run Go on Chrome OS.
Please note this has only been tested on a 64GB LTE Pixel, however it should work on other Chromebooks. Note that enabling developer mode reduces the security guarantees offered by Chrome OS.

# Install Go
First download the latest version of Go for Linux from the [Go Downloads page](https://go.dev/dl/).
After that, open a shell by hitting (CTRL+ALT+T) and typing in `shell` then hit enter. Then extract it using the following command (when replacing `< Go Linux package >` with the name of the file you downloaded):

```
sudo tar xpvf ~/Downloads/< Go Linux package > -C /usr/local
```

Go should now be installed you can test this by typing `/usr/local/go/bin/go`. If it installed correctly, you should see the Go help prompt. Go is now installed.

# Create a Workspace
To keep this simple just create a folder called `/usr/local/go/work`. Also, create a folder called `src` inside `/usr/local/go/work/`.

# Set PATH
Add the following to `~/.bashrc`:
```
export GOPATH="/usr/local/go/work"
export PATH="${PATH}:/usr/local/go/bin:${GOPATH}/bin"
```
This will allow you to run your Go programs in your shell.

# Test if it worked
First create a folder inside of your `/usr/local/go/src` folder. After that create a file in your folder called `hello.go` with the following in it:
```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, Chrome OS!")
}
```
Now, run `go install hello`. Then, run `${GOPATH}/bin/hello` (or just `hello` if you setup your GOPATH above) and you should see `Hello, Chrome OS!`.
***

# Reporting bugs
Please go to [Issues](https://github.com/golang/go/issues) to report any issues you have.
