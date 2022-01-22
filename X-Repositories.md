The `golang.org/x/...` repositories are part of the Go Project but outside the main Go tree.

They are developed under looser [compatibility requirements](https://go.dev/doc/go1compat) than the Go core.  In general, they will support the previous two releases and tip.

These repositories should have no third-party dependencies apart from other golang.org/x/... repositories. The only exceptions are [golang.org/x/tools/gopls](https://pkg.go.dev/golang.org/x/tools/gopls), [golang.org/x/vscode-go](https://go.googlesource.com/vscode-go), and [golang.org/x/pkgsite](https://pkg.go.dev/golang.org/x/pkgsite). If you would like to add a new dependency to an x repository, please [file an issue](https://github.com/golang/go/issues/new) and cc [@rsc](http://github.com/rsc) and [@andybons](https://github.com/andybons).

Install them with "go get".

  * [[docs](https://pkg.go.dev/golang.org/x/tools)] [[source](https://go.googlesource.com/tools)] ` golang.org/x/tools ` — godoc, vet, cover, and other tools.
  * [[docs](https://pkg.go.dev/golang.org/x/mobile)] [[source](https://go.googlesource.com/mobile)] ` golang.org/x/mobile ` — libraries and build tools for Go on Android.

  * [[docs](https://pkg.go.dev/golang.org/x/crypto)] [[source](https://go.googlesource.com/crypto)] ` golang.org/x/crypto ` — additional cryptography packages.
  * [[docs](https://pkg.go.dev/golang.org/x/image)] [[source](https://go.googlesource.com/image)] ` golang.org/x/image ` — additional imaging packages.
  * [[docs](https://pkg.go.dev/golang.org/x/net)] [[source](https://go.googlesource.com/net)] ` golang.org/x/net ` — additional networking packages.
  * [[docs](https://pkg.go.dev/golang.org/x/sys)] [[source](https://go.googlesource.com/sys)] ` golang.org/x/sys ` — for low-level interactions with the operating system.
  * [[docs](https://pkg.go.dev/golang.org/x/text)] [[source](https://go.googlesource.com/text)] ` golang.org/x/text ` — packages for working with text.

  * [[docs](https://pkg.go.dev/golang.org/x/blog)] [[source](https://go.googlesource.com/blog)] ` golang.org/x/blog ` — the content and server program for [blog.golang.org](https://go.dev/blog).


  * [[docs](https://pkg.go.dev/golang.org/x/review)] [[source](https://go.googlesource.com/review)] ` golang.org/x/review ` — tools for code review.
  * [[docs](https://pkg.go.dev/golang.org/x/benchmarks)] [[source](https://go.googlesource.com/benchmarks)] ` golang.org/x/benchmarks `

  * [[docs](https://pkg.go.dev/golang.org/x/exp)] [[source](https://go.googlesource.com/exp)] ` golang.org/x/exp ` — experimental code (handle with care).

[List of all packages in sub-repositories](https://pkg.go.dev/golang.org/x)
