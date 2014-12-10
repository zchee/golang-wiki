# Building windows go programs on linux

I use linux/386, but, I suspect, this procedure will apply to other host platforms as well.

First step is to build host version of go:

```
$ cd $GOROOT/src
$ ./make.bash
```

Next you need to build the rest of go compilers and linkers. I have small program to do that:

```
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

```
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

```
$ ~/bin/buildpkg windows 386
```

to build windows/386 version of Go commands and packages. You can, probably, see it from my script, I exclude building of any cgo related parts - these will not work for me, since I do not have correspondent gcc cross-compiling tools installed. So I just skip those.

Now we're ready to build our windows executable:

```
$ cat hello.go
package main

import "fmt"

func main() {
        fmt.Printf("Hello\n")
}
$ GOOS=windows GOARCH=386 go build -o hello.exe hello.go
```

We just need to find Windows computer to run our hello.exe.