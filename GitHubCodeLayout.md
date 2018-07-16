## Introduction

A common use case is to create a reusable library and an application that consumes it, and host both on GitHub.  We will illustrate this with a trivial application called "` uselessd `" that consumes a likewise trivial library called "` useless `".


## Code Layout

The app and both libraries live on GitHub, each in its own repository.  ` $GOPATH ` is the root of the _project_ - each of your GitHub repos will be checked out several folders below ` $GOPATH `.

Your code layout would look like this:

```
$GOPATH/
    src/
        github.com/
            jmcvetta/
                useless/
                    .git/
                    useless.go
                    useless_test.go
                    README.md
                uselessd/
                    .git/
                    uselessd.go
                    uselessd_test.go
                    README.md
```

Each folder under ` src/github.com/jmcvetta/ ` is the root of a separate git checkout.


## $GOPATH

Your ` $GOPATH ` variable will point to the root of your Go workspace, as described in [How to Write Go Code](http://golang.org/doc/code.html).


## Note for Eclipse Users

Both Go and Eclipse use the term "workspace", but they use it to mean something different.  What Go calls a "workspace" is what Eclipse calls a "project".  Whenever this document uses either term, it refers to a Go workspace.


### Setup the Workspace

Let's assume we are starting from scratch.  Initialize the two new repositories on GitHub, using the "Initialize this repository with a README" option so your repos can be cloned immediately.  Then setup the project like this:

```sh
cd ~/workspace # Standard location for Eclipse workspace
mkdir mygo # Create your Go workspace
export GOPATH=~/workspace/mygo # GOPATH = Go workspace
cd $GOPATH
mkdir -p src/github.com/jmcvetta
cd src/github.com/jmcvetta
git clone git@github.com:jmcvetta/useless.git
git clone git@github.com:jmcvetta/uselessd.git
```

## Libraries

Conventionally, the name of the repository is the same as the name of the package it contains.  Our ` useless ` repo contains ` useless.go ` which defines ` package useless `:

```Go
package useless

func Foobar() string {
	return "Foobar!"
}
```


## Applications

An application - Go code that will be compiled into an executable command - always defines ` package main ` with a ` main() ` function.

So ` uselessd.go ` looks like this:

```Go
package main

import (
	"net/http"

	"golang.org/x/net/websocket"
	"github.com/jmcvetta/useless"
)

func main() {
	http.Handle("/useless", websocket.Handler(func(ws *websocket.Conn) {
		ws.Write([]byte(useless.Foobar()))
	}))
	http.ListenAndServe(":3000", nil)
}
```


## Dependencies

Your project will probably depend on some existing packages.  The application above depends upon ` golang.org/x/net/websocket `.  You can install all dependencies by running "` go get -v ./... `" from the root of your workspace.  The "` go get `" command is similar to "` go install `" in that it will attempt to build and install all packages in the workspace (technically, all packages matched by "` ./... `"), except that it will also examine their dependencies and download (and install) any that are missing first.

See the output of "` go help packages `" for a full explanation of the "` ... `" syntax.

All dependencies will be installed alongside your code under "` $GOPATH/src `".  All GitHub repositories checked out by "` go get `" will use the read-only ` https:// ` repository by default.  To push changes back to GitHub from one of these repositories, change the "` origin/master `" ref in ` .git/config ` to match the SSH repository from GitHub.

## Build

During development, you can build the ` useless ` library by itself with the command "` go build ...useless `".  You could also give the full path to the package name, "` go build github.com/jmcvetta/useless `".

To compile ` uselessd.go ` and its dependencies into an executable, use the command "` go build ...uselessd `".

## Example Code

FWIW all the repo addresses on this page are real, and the ` uselessd ` application should compile if you follow the directions above.
