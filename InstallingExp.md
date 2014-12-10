First, make sure you have your workspace set up (setting ` GOPATH `). See the [How to write Go code](http://golang.org/doc/code.html) document for details.

# Installing ` exp ` under ` GOPATH `

Recently, packages under exp is moved to the go.exp sub-repository.
They should be go-gettable without any special handling.

For example,
```
go get code.google.com/p/go.exp/inotify
```