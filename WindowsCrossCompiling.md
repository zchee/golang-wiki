# Building windows go programs on linux

See [here](https://golang.org/doc/install/source#environment) for available `GOOS` and `GOARCH` values.

## Go version >= 1.5

Since Go version 1.5 cross-compiling has become very easy. Try it out with the code below. More can be found at this blog post by [Dave Cheney][1].

[1]: http://dave.cheney.net/2015/08/22/cross-compilation-with-go-1-5

```go
$ cat hello.go
package main

import "fmt"

func main() {
        fmt.Printf("Hello\n")
}
$ GOOS=windows GOARCH=386 go build -o hello.exe hello.go
```

You can now run `hello.exe` on a Windows machine near you. 

Note that the command above will silently rebuild most of standard library, and for this reason will be quite slow. To speed-up the process, you can install all the windows-amd64 standard packages on your system with

```
GOOS=windows GOARCH=amd64 go install
```

## Older Go version (<1.5)

I use linux/386, but, I suspect, this procedure will apply to other host platforms as well.

Preparation (if needed):
```sh
sudo apt-get install gcc
export go env GOROOT
```

First step is to build host version of go:

```sh
cd $GOROOT/src
sudo -E GOOS=windows GOARCH=386 PATH=$PATH ./make.bash
```

Next you need to build the rest of go compilers and linkers. I have small program to do that:

```sh
$ cat ~/bin/buildcmd
#!/bin/sh
set -e
for arch in 8 6; do
	for cmd in a c g l; do
		go tool dist install -v cmd/$arch$cmd
	done
done
exit 0
```

Last step is to build windows versions of standard commands and libraries. I have small script for that too:

```sh
$ cat ~/bin/buildpkg
#!/bin/sh
if [ -z "$1" ]; then
	echo 'GOOS is not specified' 1>&2
	exit 2
else
	export GOOS=$1
	if [ "$GOOS" = "windows" ]; then
		export CGO_ENABLED=0
	fi
fi
shift
if [ -n "$1" ]; then
	export GOARCH=$1
fi
cd $GOROOT/src
go tool dist install -v pkg/runtime
go install -v -a std
```

I run it like that:

```sh
$ ~/bin/buildpkg windows 386
```

to build windows/386 version of Go commands and packages. You can, probably, see it from my script, I exclude building of any cgo related parts - these will not work for me, since I do not have correspondent gcc cross-compiling tools installed. So I just skip those.

Now we're ready to build our windows executable:

```go
$ cat hello.go
package main

import "fmt"

func main() {
        fmt.Printf("Hello\n")
}
$ GOOS=windows GOARCH=386 go build -o hello.exe hello.go
```

We just need to find Windows computer to run our hello.exe.