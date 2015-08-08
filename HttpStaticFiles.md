# Serving Static Files with HTTP

The HTTP package provides good support for efficiently serving static files.

This is a complete Go webserver serving static files:

```
package main

import "net/http"

func main() {
	panic(http.ListenAndServe(":8080", http.FileServer(http.Dir("/usr/share/doc"))))
}
```

That example is intentionally short to make a point.  Using panic() to deal with an error is probably too aggressive & would produce too much output.  More typical style would be:

See the [net/http documentation](http://golang.org/pkg/net/http/) and in particular the [FileServer example](http://golang.org/pkg/net/http/#example_FileServer) for more details.