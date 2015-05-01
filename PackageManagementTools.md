This page contains a list of tools for managing Go packages and their dependencies. The tools are divided into categories based on their approach to version management.

The approach [endorsed by the Go project](http://golang.org/doc/faq#get_version) is "vendoring" (described below) and [godep](https://github.com/tools/godep) is a well-maintained tool for managing vendored dependencies.

## Vendoring
Vendoring takes the 3rd party source code that is referenced in your project and makes a copy of that code inside a new folder within the project. All the code your project needs is inside the one project repository. Vendoring also provides a performance enhancement on getting the code because only one url call is required.

| **gigo**  |https://github.com/LyricalSecurity/gigo|
|:----------|:-----------------------------|
|Title      |Helps provide go get support for private repositories, pip for golang|
|Author     |Lyrical Security                  |
|Categories |Vendoring, Revision Locking   |
|           |                              |
| **godep** |https://github.com/tools/godep|
|Title      |Helps build packages reproducibly by fixing their dependencies|
|Author     |Keith Rarick                  |
|Categories |Vendoring, Revision Locking (git, mercurial, bazaar)|
|           |                              |
| **gom**   |https://github.com/mattn/gom  |
|Title      |Go Manager - bundle for go    |
|Author     |Yasuhiro Matsumoto            |
|Categories |Vendoring/Bundling            |
|           |                              |
| **goop**  |https://github.com/nitrous-io/goop|
|Title      |A dependency manager for Go (golang), inspired by Bundler.|
|Author     |Nitrous.IO                    |
|Categories |Vendoring, Revision Locking   |
|           |                              |
| **third-party** |https://github.com/coreos/third_party.go|
|Title      |Self contained GOPATH helper  |
|Author     |CoreOS                        |
|Categories |Vendoring                     |
|Notes      |CoreOS now uses github.com/tools/godep|
|           |                              |
| **vendorize** |https://github.com/kisielk/vendorize|
|Author     |Kamil Kisiel                  |
|Categories |Vendoring                     |
|           |                              |
| **party** |https://github.com/mjibson/party|
|Author     |Matt Jibson                   |
|Categories |Vendoring                     |
|           |                              |
| **prewrite** |https://github.com/dmitris/prewrite|
|Author     |Dmitry Savintsev                      |
|Categories |Vendoring                             |
|           |                                      |
| **vendor** |https://github.com/kardianos/vendor|
|Author     |Daniel Theophanes                   |
|Categories |Vendoring                     |
|           |                              |
| **bunch** |https://github.com/dkulchenko/bunch|
|Title     |npm-like tool for managing Go dependencies|
|Author     |Daniil Kulchenko                   |
|Categories |Vendoring/Bundling/Revision Locking     |
|           |                              |
| **gondler** |https://github.com/rosylilly/gondler|
|Title      |Bundler for golang            |
|Author     |Sho Kusano                    |
|Categories |Vendoring/Bundling/Revision Locking. Requires Ruby|

## Revision Locking
Revision Locking creates a dependency file that references specific commits in the different version control systems the code is located in. Just like vendoring, the RL tool is used to get, build and install your project. One advantage is that your project repository continues to only contain the specific project code.

| **dondur** |https://github.com/oguzbilgic/dondur|
|:-----------|:-----------------------------|
|Title       |Freeze your Go dependencies with ease|
|Author      |Oguz Bilgic                   |
|Categories  |Revision Locking (git, mercurial, bazaar)|
|            |                              |
| **envie**  |https://github.com/sam-falvo/envie|
|Title       |Download and manage Go projects and their dependencies|
|Author      |Samuel A. Falvo II            |
|Categories  |Revision Locking (unknown)    |
|            |                              |
| **glide**  |https://github.com/Masterminds/glide|
|Title       |Simplified Go workspace and dependency management.|
|Author      |Matt Butcher and Matt Farina  |
|Categories  |Vendoring, Revision Locking (git, mercurial, bzr, svn)    |
|            |                              |
| **glock**  |https://github.com/robfig/glock|
|Title       |Lock dependencies to specific revisions.|
|Author      |Rob Figueiredo                |
|Categories  |Revision Locking (git)        |
|            |                              |
| **gobs**   |https://bitbucket.org/vegansk/gobs|
|Title       |Build system and package manager for go language|
|Author      |Anatoly Galiulin              |
|Categories  |Revision Locking (git)        |
|            |                              |
| **godep**  |https://github.com/tools/godep|
|Title       |Helps build packages reproducibly by fixing their dependencies|
|Author      |Keith Rarick                  |
|Categories  |Vendoring, Revision Locking (git, mercurial, bazaar)|
|            |                              |
| **godeps** |https://launchpad.net/godeps  |
|Title       |Print, fetch and update dependencies with care. In production use by Canonical. The first tool with this name!|
|Author      |Roger Peppe                   |
|Categories  | Revision Locking (git, mercurial, bzr)|
| **gopack** |https://github.com/d2fn/gopack|
|Title       |Dependency management for go inspired by rebar|
|Author      |Dietrich Featherston          |
|Categories  |Revision Locking (git)        |
|            |                              |
| **gopin**  |https://github.com/laher/gopin|
|Title       |Experimental go-get fork with support for tags and alternative repos|
|Author      |Go Package Manager            |
|Categories  |Revision Locking (git)        |
|            |                              |
| **gopm**   |https://github.com/GPMGo/gopm |
|Title       |Tool for search, install, update, share packages in Go|
|Author      |Am Laher                      |
|Categories  |Revision Locking (git, mercurial, bazaar)|
|            |                              |
| **gpm**    |https://github.com/pote/gpm   |
|Title       |Barebones dependency manager for Go.|
|Author      |Pablo Astigarraga             |
|Categories  |Revision Locking (git, mercurial, bazaar)|
|            |                              |
| **johnny deps** |https://github.com/VividCortex/johnny-deps|
|Title       |Barebones dependency manager for Go|
|Author      |Baron Schwartz / Gustavo Kristic|
|Categories  |Revision Locking (git)        |
|            |                              |
| **pack**   |https://github.com/theplant/pak|
|Title       |Simple package management tool for Go|
|Author      |The Plant                     |
|Categories  |Revision Locking (git)        |
|            |                              |
| **rx**     |http://godoc.org/kylelemons.net/go/rx|
|Title       |[Automation for dependency management tasks](http://kylelemons.net/blog/2012/04/22-rx-for-go-headaches.article)|
|Author      |Kyle Lemons                   |
|Categories  |Revision Locking (git, mercurial)|
|            |                              |
| **wgo**    |https://github.com/skelterjohn/wgo|
|Title       |Managed workspaces on top of the go tool|
|Author      |John Asmuth                   |
|Categories  |Revision Locking (git, extensible)|

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

| **gvm** |https://github.com/moovweb/gvm|
|:--------|:-----------------------------|
|Title    |Go Version Manager            |
|Author   |Josh Bussdieker               |
|Categories|Go Version Manager           |

| **goenv**  | https://bitbucket.org/ymotongpoo/goenv |
|:-----------|:---------------------------------------|
| Title      | Go environment manager                 |
| Author     | Yoshifumi YAMAGUCHI                    |
| Categories | Go Version Manager                     |

## Unclassified
Not able to classify these tools.

| **go-dep** |https://github.com/go-dep/dep|
|:-----------|:----------------------------|
|Title       |Go package dependencies with the help of the Go Dependency Format (GDF)|
|Author      |Marc Rene Arns               |
|Categories  |Not Sure                     |

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