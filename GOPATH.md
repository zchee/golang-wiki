# Introduction

The GOPATH environment variable is used to specify directories outside of $GOROOT that contain the source for Go projects and their binaries.

See the [go command](http://golang.org/cmd/go/#hdr-GOPATH_environment_variable) and [go/build package](http://golang.org/pkg/go/build/) documentation for more details.

Since the $GOPATH variable can be a list, the rest of this document will use $GOPATH to mean the first element unless otherwise specified.

## Integrating GOPATH

On OS X or Linux (bash), adding the following expression to PATH will add all $GOPATH/bin directories.
```
${GOPATH//://bin:}/bin
```

## Directory layout

The source for a package with the import path ` "X/Y/Z" ` is in the directory
```
$GOPATH/src/X/Y/Z
```

The binary for a package with the import path ` "X/Y/Z" ` is in
```
$GOPATH/pkg/$GOOS_$GOARCH/X/Y/Z.a
```

The binary for a command whose source is in ` $GOPATH/src/A/B ` is
```
$GOPATH/bin/B
```

## Repository integration and creating "go gettable" projects
When fetching a package the go tool looks at the package's import path to discover a URL. For instance, if you attempt to
```
go get github.com/go-kit/kit
```
the go tool will get the source from the project hosted at https://github.com/go-kit/kit/. It will clone the repository to
```
$GOPATH/src/github.com/go-kit/kit
```

As a result, if (from your repository project) you import a package that is in the same repository, you need to use its "full" import path - the place "go get" puts it. In this example, if something else wants to import the "kit" package, it should import "github.com/go-kit/kit" rather than "kit".

## Tips and tricks

### Use a single GOPATH

Even though the GOPATH may be a list of directories, it is generally sufficient to use a single GOPATH for all Go code on your machine.  Since all packages retrieved with "go get" have a unique URL (and thus a unique path on disk), having more than one GOPATH is almost never necessary when building with the Go tool.

## FAQ
### Why won't ` $GOPATH/src/cmd/mycmd/*.go ` build?
When the go command is looking for packages, it always looks in ` $GOROOT ` first.  This includes directories, so if it finds (as in the case above) a ` cmd/ ` directory in ` $GOROOT ` it won't proceed to look in any of the GOPATH directories.  This prevents you from defining your own ` math/matrix ` package as well as your own ` cmd/mycmd ` commands.