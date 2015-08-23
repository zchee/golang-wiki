This page contains a list of tools for managing Go packages and their dependencies. The tools are divided into categories based on their approach to version management.

## GO15VENDOREXPERIMENT

As of [June 19th, 2015](https://groups.google.com/d/msg/golang-dev/74zjMON9glU/EOKSoaL5p8wJ), the Go toolchain includes an experimental vendoring flag, `GO15VENDOREXPERIMENT`. This is now part of the Go 1.5 release and represents the Go team's recommended approach to vendoring dependencies. You can read more about how this environment variable works in the [Go 1.5 documentation](https://golang.org/cmd/go/#hdr-Vendor_Directories) and the [original design document](https://docs.google.com/document/d/1Bz5-UB7g2uPBdOx-rw5t9MxJwkfpx90cqG9AFL0JAYo/view). For a more detailed explanation, check out [this post](https://medium.com/@freeformz/go-1-5-s-vendor-experiment-fd3e830f52c3) by [@freeformz](https://twitter.com/freeformz).

Tools supporting this feature include:

 * [Godep](https://github.com/tools/godep)
 * [Govendor](https://github.com/kardianos/govendor)
 * [Glide](https://github.com/Masterminds/glide)
 * [godm](https://github.com/hectorj/godm)
 * [vexp](https://github.com/kr/vexp)
 * [gv](https://github.com/forestgiant/gv)

## Pkg copy with import path re-write
Vendoring takes the 3rd party source code that is referenced in your project and makes a copy of that code inside a new folder within the project. It re-writes the import paths so there is a single copy of all packages. GOPATH is not modified at any time.

| **party** |https://github.com/mjibson/party|
|:----------|:-----------------------------|
|Author     |Matt Jibson                   |
|Categories |Vendoring, Copies into "_third_party". Does not analyze dependencies first. No inspection.|
|           |                              |
| **govendor** |https://github.com/kardianos/govendor|
|Title      |Copy, re-write, and list dependent package status.|
|Author     |Daniel Theophanes                   |
|Categories |Pkg Copy,Import rewrite, record VCS version. Copies into "internal" or "vendor".      |
|           |                              |
| **vendorize** |https://github.com/kisielk/vendorize|
|Author     |Kamil Kisiel                  |
|Categories |Vendoring. Copies into "3rdparty".                     |
|           |                              |
| **nut** |https://github.com/jingweno/nut|
|Author     |Jingwen Owen Ou                  |
|Categories |Pkg Copy & Import rewrite. Copies into "vendor".                     |

## Pkg copy, build using GOPATH modification, supports fetching specific version
Copy packages locally. When building modify the GOPATH to reference the local package store. Not only records specific version, but also fetches specific version.

| **gopm**   |https://github.com/GPMGo/gopm |
|:----------|:-----------------------------|
|Title       |Tool for search, install, update, share packages in Go|
|Author      |Am Laher                      |
|Categories  |Revision Locking (git, mercurial, bazaar). Copies into ".vendor/src".|
|           |                              |
| **gom**   |https://github.com/mattn/gom  |
|Title      |Go Manager - bundle for go    |
|Author     |Yasuhiro Matsumoto            |
|Categories |Vendoring/Bundling. Copies into "_vendor/src"          |
|           |                              |
| **bunch** |https://github.com/dkulchenko/bunch|
|Title     |npm-like tool for managing Go dependencies|
|Author     |Daniil Kulchenko                   |
|Categories |Vendoring/Bundling/Revision Locking. Copies into ".vendor". Does NOT fully support windows.|
|           |                              |
| **goop**  |https://github.com/nitrous-io/goop|
|Title      |A dependency manager for Go (golang), inspired by Bundler.|
|Author     |Nitrous.IO                    |
|Categories |Vendoring, Revision Locking. Copies into ".vendor/src". Does NOT fully support windows.   |

## Pkg copy, build using GOPATH  modification
Copy packages locally. When building modify the GOPATH to reference the local package store.

| **godep** |https://github.com/tools/godep|
|:----------|:-----------------------------|
|Title      |Helps build packages reproducibly by fixing their dependencies|
|Author     |Keith Rarick                  |
|Categories |Vendoring, Version Recording. Copies into "Godep/_workspace/src".|
|           |                              |
| **wgo**    |https://github.com/skelterjohn/wgo|
|Title       |Managed workspaces on top of the go tool|
|Author      |John Asmuth                   |
|Categories  |local GOPATH can be configured.|
|           |                              |
| **glide** |https://github.com/Masterminds/glide|
|Title      |Project-based workspaces and dependency management|
|Author     |Matt Butcher and Matt Farina     |
|Categories |Project workspaces, vendoring, version locking. Manages dependencies in _vendor using a sub-shell|
|           |                              |
| **gb** |http://getgb.io/|
|Title      |Project-based workspaces and dependency management|
|Author     |Dave Cheney     |
|Categories |Project-based workspaces, vendoring, version locking. Manages dependencies in /vendor/src|

## Revision Locking
Package source control versions are recorded. Versions are updated into the GOPATH package tree.
Requires switching GOPATH for every project.

| **glock**  |https://github.com/robfig/glock|
|:-----------|:-----------------------------|
|Title       |Lock dependencies to specific revisions.|
|Author      |Rob Figueiredo                |
|Categories  |Revision Locking (git)        |
|            |                              |
| **gobs**   |https://bitbucket.org/vegansk/gobs|
|Title       |Build system and package manager for go language|
|Author      |Anatoly Galiulin              |
|Categories  |Revision Locking (git). Requires bash, no Windows support.       |
|            |                              |
| **godeps** |https://launchpad.net/godeps  |
|Title       |Print, fetch and update dependencies with care. In production use by Canonical. The first tool with this name!|
|Author      |Roger Peppe                   |
|Categories  | Revision Locking (git, mercurial, bzr)|
|            |                              |
| **gopack** |https://github.com/d2fn/gopack|
|Title       |Dependency management for go inspired by rebar|
|Author      |Dietrich Featherston          |
|Categories  |Revision Locking (git)        |
|            |                              |
| **gopin**  |https://github.com/laher/gopin|
|Title       |Experimental go-get fork with support for tags and alternative repos|
|Author      |Go Package Manager            |
|Categories  |Revision Locking (git)        |
|           |                              |
| **gigo**  |https://github.com/LyricalSecurity/gigo|
|Title      |Helps provide go get support for private repositories, pip for golang|
|Author     |Lyrical Security                  |
|Categories |Vendoring, Revision Locking (git). Does not appear to copy files.  |


## Vendor Utilities
Not full vendor tool, but may still provide value.

| **prewrite** |https://github.com/dmitris/prewrite|
|:-----------|:-----------------------------|
|Author     |Dmitry Savintsev                      |
|Categories |Import re-writer, add or remove specified prefix                             |

## Import Proxies
Import Proxies act as a man in the middle between the Go tool and the VCS. It parses the data stream while the repository is being cloned.

| **git-version-proxy** |https://github.com/msiebuhr/git-version-proxy|
|:----------------------|:--------------------------------------------|
|Title                  |A HTTP Git proxy that only exposes certain versions|
|Author                 |Morten Siebuhr                               |
|Categories             |Import Proxy (git)                           |
|                       |                                             |
| **gopkg.in**          |https://gopkg.in                             |
|Title                  |Redirect the go tool onto well defined GitHub repositories. Versioning with tags and branches or the repository name.|
|Author                 |Gustavo Niemeyer                             |
|Categories             |Import Proxy (GitHub)                        |

## Go Version Managers
Go Version Managers allow you to have multiple versions of Go installed on your machine. It allows you to switch between those versions.

| **goenv**  | https://bitbucket.org/ymotongpoo/goenv |
|:-----------|:---------------------------------------|
| Title      | Go environment manager                 |
| Author     | Yoshifumi YAMAGUCHI                    |
| Categories | Go Version Manager                     |


## Client App Test Packages
Here is a list of packages that authors can use to test their tools against.

| **beego-mgo** |https://github.com/goinggo/beego-mgo|
|:--------------|:-----------------------------------|
|Author         |Bill Kennedy                        |
|Desc           |Sample Application For Using the Beego web framework with MGO|
|               | |
| **revel-mgo** |https://github.com/goinggo/revel-mgo|
|Author         |Bill Kennedy                        |
|Desc           |Sample revel project with mgo support|

## Abandoned Tools
 * https://github.com/coreos/third_party.go
 * http://godoc.org/kylelemons.net/go/rx
 * https://github.com/theplant/pak

## Not Written in Go
These tools are recorded for completeness, but it is suggested not to use them as they are platform specific.
 * https://github.com/rosylilly/gondler
 * https://github.com/VividCortex/johnny-deps
 * https://github.com/moovweb/gvm
 * https://github.com/pote/gpm