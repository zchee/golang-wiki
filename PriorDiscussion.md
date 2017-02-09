# Prior Discussion

## Background

This page links to prior discussion on various topics.

The page complements the [official FAQ](https://golang.org/doc/faq). While the official FAQ contains things which are frequently asked and contains answers, this page contains things that have been repeatedly asked, but maybe not frequently, and only needs to link to one or more previous threads.  Over time, these entries may graduate to entries in the official FAQ.

**Editors:** When editing this page, please don't change the titles of sections, as that breaks the #anchors in URLs. You can rearrange, though. Feel free to add entries at will. There is no requirement for code or English review here.

## Asked Questions & Prior Discussion

### Panics on sends or closes of closed channel

See https://github.com/golang/go/issues/11344#issuecomment-117862884

### Thread-local, Goroutine-local storage

TODO

### Add explicit int-to-bool conversions

Rejected, see 
https://github.com/golang/go/issues/9367#issuecomment-143128337

### Add mechanism to silence vet warnings

Rejected, see discussion in https://github.com/golang/go/issues/17058

### Add vet warning for unused function arguments

Rejected, see https://github.com/golang/go/issues/7892#issuecomment-66094282

### Make go get more verbose / add a progress bar

Rejected, see
https://github.com/golang/go/issues/17959
https://github.com/golang/go/issues/18388#issuecomment-268315634

### Shorten error handling / return sugar

Rejected, see
https://github.com/golang/go/issues/16225

### Support symlinks in go toolchain / environment variables

Rejected, see
https://github.com/golang/go/issues/15507

### Make unused imports/variables a warning, not an error

Rejected.

### Add warnings to the Go compiler

Rejected.

### Weak references

Unlikely to be added. See discussion at https://groups.google.com/forum/#!topic/golang-nuts/PYWxjT2v6ps, and https://groups.google.com/forum/?pli=1#!topic/golang-nuts/MMWXRANh0-g which points out that `sync.Pool` is a specific form of weak reference.