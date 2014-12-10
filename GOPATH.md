# Introduction

The GOPATH environment variable is used to specify directories outside of $GOROOT that contain the source for Go projects and their binaries.

See the [go command](http://golang.org/cmd/go/#hdr-GOPATH_environment_variable) and [go/build package](http://golang.org/pkg/go/build/) documentation for more details.

Since the $GOPATH variable can be a list, the rest of this document will use $GOPATH to mean the first element unless otherwise specified.

## Integrating GOPATH

On OS X or Linux, adding the following expression to PATH will add all $GOPATH/bin directories.
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

## Repository Integration and Creating "go gettable" Projects
When fetching a package the go tool looks at the package's import path to discover a URL. For instance, if you attempt to
```
go get code.google.com/p/gomatrix/matrix
```
the go tool will get the source from the project hosted at http://code.google.com/p/gomatrix/. It will clone the repository to
```
$GOPATH/src/code.google.com/p/gomatrix
```

As a result, if (from your repository project) you import a package that is in the same repository, you need to use its "full" import path - the place "go get" puts it. In this example, if something else wants to import the "matrix" package, it should import "code.google.com/p/gomatrix/matrix" rather than "matrix".

## Tips and tricks

### Third-party Packages
It is useful to have two GOPATH entries. One for a location for 3rd party goinstalled packages, and the second for your own projects. List the 3rd party GOPATH first, so that goinstall will use it as a default destination. Then you can work in the second GOPATH directory and have all your packages be importable by using the "go" command, goinstall, or a GOPATH-aware 3rd party build tool like [gb](http://code.google.com/p/go-gb).

## FAQ
### Why won't ` $GOPATH/src/cmd/mycmd/*.go ` build?
When the go command is looking for packages, it always looks in ` $GOROOT ` first.  This includes directories, so if it finds (as in the case above) a ` cmd/ ` directory in ` $GOROOT ` it won't proceed to look in any of the GOPATH directories.  This prevents you from defining your own ` math/matrix ` package as well as your own ` cmd/mycmd ` commands.