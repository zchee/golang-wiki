With Go 1.5, Go will support mobile platforms (Android and iOS) and
will provide tools to build mobile applications.

There are two strategies you can follow to include Go into
your mobile stack:

- Writing all-Go native mobile applications.
- Writing SDK applications by generating bindings from a Go package and invoke them from Java (on Android) and Objective-C (on iOS).

This article will contain step-by-step guides to explain how to achieve
these strategies.

## Tooling

Go Mobile introduces a new tool, gomobile, to help you with the build
and the binding process. Go get gomobile and initialize it to install
the required toolchain.

On Mac OSX, you will need to have
[Xcode Command Line Tools](https://developer.apple.com/downloads/)
installed.

```
$ go get golang.org/x/mobile/cmd/gomobile
$ gomobile init # it might take a few minutes
```

(The following sections will help you how to use the gomobile tool.)

## Native applications

TBD

## SDK applications and generating bindings

TBD