This page documents the file tree for a source installation of go1.13.1.

```
$ tree -d -L 2 /usr/lib/go1.13.1 | head
/usr/lib/go1.13.1
`-- go
    |-- api
    |-- bin
    |-- doc
    |-- lib
    |-- misc
    |-- pkg
    |-- src
    `-- test
$
```

api contains data for Go's API checker

```
$ ls $GOROOT/api
README	    go1.10.txt	go1.13.txt  go1.4.txt  go1.7.txt  go1.txt
except.txt  go1.11.txt	go1.2.txt   go1.5.txt  go1.8.txt  next.txt
go1.1.txt   go1.12.txt	go1.3.txt   go1.6.txt  go1.9.txt
$
```

bin contains the go and gofmt executables

```
$ ls -l $GOROOT/bin
total 11576
-rwxr-xr-x 1 root root 9652760 Oct  2 03:02 go
-rwxr-xr-x 1 root root 2197756 Oct  2 03:02 gofmt
$
```

doc contains .css, .go, .html, .js, and .png files

lib contains the compressed time zone database

```
$ tree $GOROOT/lib | head -n 5
/usr/lib/go1.13.1/go/lib
`-- time
    |-- README
    |-- update.bash
    `-- zoneinfo.zip
$
```

misc contains files pertaining to specific build modes and platforms

```
$ tree -d -L 1 $GOROOT/misc | head -n 12
/usr/lib/go1.13.1/go/misc
|-- android
|-- arm
|-- cgo
|-- chrome
|-- ios
|-- linkcheck
|-- nacl
|-- reboot
|-- swig
|-- trace
`-- wasm
$
```

pkg contains libs, header files, compiled object files, and executables

```
$ tree -d -L 1 $GOROOT/pkg | head -n 6
/usr/lib/go1.13.1/go/pkg
|-- include
|-- linux_386
|-- linux_386_dynlink
|-- obj
`-- tool
$
```
src contains the go1.13.1 source code

test contains tests of the Go toolchain and runtime