This wiki page documents the file tree for a source installation of go1.9.2 to which have been added the github.com/golang blog, net and tools sub-repositories, and the github.com/gonum/gonum repository. It is somewhat consistent with the file tree of the golang.org/dl pre-compiled downloads for GNU/Linux. It presumes the reader is familiar with utilisation of $GOPATH on Un*x as a colon-separated string; GNU/Linux being a multi-user OS the added sub-repositories and repository are located in $HOME/go and /usr/share/gocode.

```
% tree -d -L 2 /usr/lib/go1.9.2 | head
/usr/lib/go1.9.2
`-- go
    |-- api
    |-- bin
    |-- doc
    |-- lib
    |-- misc
    |-- pkg
    |-- src
    `-- test
%
```

api contains data for Go's API checker

```
% ls $GOROOT/api
README     go1.1.txt  go1.3.txt  go1.5.txt  go1.7.txt go1.9.txt  next.txt
except.txt  go1.2.txt  go1.4.txt  go1.6.txt  go1.8.txt go1.txt
%
```

bin contains the go and gofmt executables

```
% ls -l $GOROOT/bin
total 7588
-rwxr-xr-x 1 root root 5918348 Oct 31 16:06 go
-rwxr-xr-x 1 root root 1831140 Oct 31 16:06 gofmt
%
```

doc contains .css, .go, .html, .js, and .png files

lib contains the compressed time zone database

```
% tree $GOROOT/lib | head -n 5
/usr/lib/go1.9.2/go/lib
`-- time
|-- README
|-- update.bash
`-- zoneinfo.zip
%
```

misc/android contains information on development for android<br/>
misc/arm contains a script for executing go binaries on android<br/>
misc/cgo contains tests and examples of cgo<br/>
misc/chrome contains a Chrome extension<br/>
misc/git contains a pre-commit hook<br/>
misc/ios contains information on cross compiling for iOS<br/>
misc/linkcheck contains a program checking links on the godoc website<br/>
misc/nacl contains Go's integration with nacl, used by the Go playground<br/>
misc/sortac contains a utility for sorting the AUTHORS and CONTRIBUTORS files<br/>
misc/swig contains examples of using Go with SWIG<br/>
misc/trace contains a generated file used by go tool trace

```
% tree -d -L 1 $GOROOT/misc | head -n 12
/usr/lib/go1.9.2/go/misc
|-- android
|-- arm
|-- cgo
|-- chrome
|-- git
|-- ios
|-- linkcheck
|-- nacl
|-- sortac
|-- swig
`-- trace
%
```

pkg contains libs, header files, compiled object files, and executables

```
% tree -d -L 1 $GOROOT/pkg | head -n 7
/usr/lib/go1.9.2/go/pkg
|-- bootstrap
|-- include
|-- linux_386
|-- linux_386_dynlink
|-- obj
`-- tool
%
```

test contains tests of the Go tool chain and runtime

the github.com/golang net and tools sub-repositories and github.com/gonum/gonum repository can be located in /usr/share/gocode, utilising the following commands

```
% su -c tcsh
Password:
# setenv GOPATH /usr/share/gocode
# go get -u golang.org/x/tools/...
# go get -u gonum.org/v1/gonum/...
# find $GOPATH -print0 | xargs -0 file | grep "executable" | grep ELF \
? | cut -f 1 -d : | xargs strip --strip-unneeded
# exit
%
```

to compile Go code with the libraries in /usr/share/gocode you must add the location to $GOPATH

```
% setenv GOPATH $HOME/go:/usr/share/gocode
% go get -u golang.org/x/blog
package golang.org/x/blog: no Go files in /home/eric/go/src/golang.org/x/blog
% cd go/src/golang.org/x/blog/blog
% go build
% mv blog $HOME/go/bin
%
```

this page utilises the C shell as [Setting GOPATH](https://github.com/golang/go/wiki/SettingGOPATH) doesn't include that shell

for information on running the blog server see [Go Blog](https://github.com/golang/blog); those instructions might be more comprehensive being edited, but for Un*x just omit the .exe
file extension