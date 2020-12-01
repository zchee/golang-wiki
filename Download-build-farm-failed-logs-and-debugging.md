The Go project has all build failed logs storage at GCE, which you can access by the [dashboard](https://build.golang.org/).

You can download all the failed logs by `fetchlogs`.

Download `fetchlogs` by `go get golang.org/x/build/cmd/fetchlogs`

`fetchlogs` only download 300 lastest failed logs by default, which is not enough for "mystery"/"flaky" bugs.
`fetchlogs -n <the number you want>`

You may also want to take a look at
`github.com/aclements/go-misc/greplogs`. It's a useful tool by Austin
to run grep over logs fetched by fetchlogs. 

Also `github.com/aclements/findflakes` can make some guesses as to when a
flaky test started failing.