# Go on NetBSD

Go on NetBSD is fairly stable on the architectures below. However, some bugs remain; see the [issue tracker](https://github.com/golang/go/issues?q=is%3Aissue+is%3Aopen+label%3AOS-NetBSD) for details.

| **Kernel version**    | **Architectures** | **Initial support version** | **Final support version** |
|:----------------------|:------------------|:----------------------------|:--------------------------|
| 8.0 or above          | amd64, arm, 386   |                             |                           |
| 7.0 through 7.1       | amd64, arm, 386   | Go 1.3 _*_                  |                           |
| 6.0 through 6.1       | amd64, arm, 386   | Go 1.3 _*_                  | Go 1.9.7                  |
| 5.0 through 5.2 (EOL) | amd64, 386        | Go 1                        | Go 1.2.2                  |

_*_ Go 1.5 or above is recommended.

Support for the arm64 architecture is a work in progress, see https://go.dev/issue/30824.

# Go packages in pkgsrc

[pkgsrc](https://pkgsrc.org/), the NetBSD package collection, contains up-to-date packages for released Go versions. The packages contain the version in the name (e.g. [`lang/go113`](http://pkgsrc.se/lang/go113)) so that multiple versions can be installed in parallel. [`lang/go`](http://pkgsrc.se/lang/go) is a meta-package that always depends on the default go version.

Note that the `go` binary name is also installed with a version suffix. Install the [`pkgtools/pkg_alternatives`](http://pkgsrc.se/pkgtools/pkg_alternatives) package to get a `go` command symlink in your PATH.

There are a number of packages for software written in Go in pkgsrc. At the moment, module-based builds are experimental, and packages are built using a GOPATH layout.

# Preparing NetBSD for Go

  * install NetBSD (remember to install pkgsrc in the last step)
  * install shells/bash and devel/git (do ` make package-install clean ` in ` /usr/pkgsrc/shells/bash ` and ` /usr/pkgsrc/devel/git `.
    * Using binary packages: ` pkgin install bash git `