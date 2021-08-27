<pre>
$ go version
go version go1.15.5 darwin/amd64
</pre>

<details><summary><code>go env</code> Output</summary><br><pre>
$ go env
GO111MODULE=""
GOARCH="amd64"
GOBIN=""
GOCACHE="/Users/prsingh/Library/Caches/go-build"
GOENV="/Users/prsingh/Library/Application Support/go/env"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="darwin"
GOINSECURE=""
GOMODCACHE="/Users/prsingh/go/pkg/mod"
GONOPROXY=""
GONOSUMDB=""
GOOS="darwin"
GOPATH="/Users/prsingh/go"
GOPRIVATE=""
GOPROXY="https://proxy.golang.org,direct"
GOROOT="/usr/local/go"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/usr/local/go/pkg/tool/darwin_amd64"
GCCGO="gccgo"
AR="ar"
CC="clang"
CXX="clang++"
CGO_ENABLED="1"
GOMOD="/Users/prsingh/Documents/chef-code-resources/non-forked/chef-workstation/components/main-chef-wrapper/go.mod"
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="-fPIC -m64 -pthread -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fdebug-prefix-map=/var/folders/zg/pm311s8n7lbcl98gj_w_cs1xxythc4/T/go-build487431618=/tmp/go-build -gno-record-gcc-switches -fno-common"

</pre></details>

my verify build on buildkite fails,
verify build fails with error log https://buildkite.com/chef/chef-chef-workstation-main-verify/builds/4925#40999136-25c5-4e5c-abd6-f2768099cd18
```
-->   windows/amd64: github.com/chef/chef-workstation/components/main-chef-wrapper
-->    darwin/amd64: github.com/chef/chef-workstation/components/main-chef-wrapper
-->     linux/amd64: github.com/chef/chef-workstation/components/main-chef-wrapper
 
1 errors occurred:
--> windows/amd64 error: exit status 1
Stderr: platform-lib/version_windows.go:22:2: cannot find package "." in:
	/src/vendor/golang.org/x/sys/windows/registry
 
```
Though it is working on buildkite adhoc build and local machine,

I updated go.mod file in the commint https://github.com/chef/chef-workstation/commit/07584108d9480093894645589cb6840019b8b387, by using command
go get -u golang.org/x/sys

Running go `get -u golang.org/x/sys/windows` gives
```
go: found golang.org/x/sys/windows in golang.org/x/sys v0.0.0-20210823070655-63515b42dcdf
package golang.org/x/sys/windows: build constraints exclude all Go files in /Users/prsingh/go/pkg/mod/golang.org/x/sys@v0.0.0-20210823070655-63515b42dcdf/windows
```

`GOOS=windows GOARCH=amd64 go get golang.org/x/sys/windows` just gives
` go: found golang.org/x/sys/windows in golang.org/x/sys v0.0.0-20210823070655-63515b42dcdf`
<!--
If possible, provide a recipe for reproducing the error.
A complete runnable program is good.
A link on play.golang.org is best.
-->


I expect buildkite build to run, and go get golang.org/x/sys/windows to work




