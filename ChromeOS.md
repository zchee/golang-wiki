# Introduction
## EDIT: You dont need to compile from source in dev mode, you can just use the version in crew. Also you can use the crostini shell which is rolling out to many devices.

This tutorial will show you how to install/build/run go on chrome OS. I have tested this using a Chromebook Pixel, however I do not have any other types of Chromebooks. However, this should work as long as you install the corresponding Linux package for your processor.

# Requirements
Your Chromebook must be in developer mode for this to work. Also please note this has only been tested on a 64gb LTE Pixel, however it should work on other Chromebooks. Note that enabling developer mode reduces the security guarantees offered by Chrome OS.

# Install Go
First download the latest version of Go for Linux-amd64 from the [Go Downloads page](http://golang.org/dl/) after that open a shell by hitting (Crtl+alt+t) and typing in "shell" then hit enter. Then extract it using the following command.

```
sudo tar -C /usr/local -xzf ~/Downloads/FILENAMEHERE
```

Go should now be installed you can test this by typing "/usr/local/go/bin/go" if it installed you should see the go help prompt. Congrats Go is now installed however you will not be able to run anything because chrome mounts partitions with noexec. The following will guide you through remounting your home folder, and setting up paths that are persistent across reboots, and shell sessions.

# Create a Workspace
To keep this simple just create a folder called "gocode" in your downloads folder. Also create a folder called "src" inside.

# Set Paths & Exec
Either type the following into your shell each session or if you want it to be persistent between sessions add it to your "~/.bashrc" file. The last line remounts your user folder so that you can run your go code other wise you would get permission errors.
```
export PATH=$PATH:/usr/local/go/bin
export GOPATH=~/Downloads/go
export PATH=$PATH:$GOPATH/bin
sudo mount -i -o remount,exec /home/chronos/user/
```
This will allow you to run your go object files in your shell.

# Test If It Worked
First add a "hello" folder inside of your "gocode/src" folder. After that create a file in your "gocode/src/hello" folder called "hello.go" with the following in it. Then run "go install hello" then "hello" and you should see "Hello, chrome os" in the console.
```go
package main

import "fmt"

func main() {
	fmt.Printf("Hello, chrome os\n")
}
```