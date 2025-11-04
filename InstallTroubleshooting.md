---
title: InstallTroubleshooting
---

## Introduction

There are many times in which you may install Go (either from source or from a binary distribution) and things don't work quite right. This page is meant to collect some common wisdom about problems that are relatively common or difficult to diagnose and provide tips and solutions.

## Contents

- [Introduction](#introduction)
- [Tips](#tips)
  - [Environment variables](#environment-variables)
- [Troubleshooting](#troubleshooting)
  - [Still need help?](#still-need-help)

## Tips

### Environment variables

There are several environment variables that can be set to configure
your Go installation: see https://pkg.go.dev/cmd/go#hdr-Environment_variables.

Normally none of them need to be set.

That said, the default for `GOROOT` is the root of your Go
installation.
The default for `GOPATH` is the directory named "go" in your home
directory.
The `GOPATH` directory should not be set to, or contain, the `GOROOT`
directory.

If you have installed Go in the "go" directory in your home directory,
running the go tool will print a warning.
You should either move the Go installation, or set the `GOPATH`
environment variable to some other directory.

For example, on a Unix system:

```
> go run hello.go
warning: GOPATH set to GOROOT (/home/username/go) has no effect
Hello, world
> GOPATH=/home/username/gopath
> export GOPATH
> go run hello.go
Hello, world
```

## Troubleshooting

##### The `go build` command doesn't do anything!

The `go build` command will only produce a binary; if you run go build in a package directory, it will build the package normally (and report any compile errors), but it will not install it. For that, you use `go install`. If you think you're building a binary and none is produced, make sure you are in package `main` and that you do not have GOBIN set.

##### Why does `go get` report `"Fetching https://runtime/cgo?go-get=1"`?

If you have a source distribution, make sure that your packages are up-to-date. Also double check the environment above.

##### When cross compiling, I get `"runtime/extern.go:135: undefined: theGoos"`

Read [WindowsCrossCompiling](WindowsCrossCompiling) for some helpful scripts. You can also use the `--no-clean` argument when you're building the cross-compile toolchain via `make.bash`.

##### Why does `go get` work for some packages and report `permission denied` in `$GOROOT` for some others (with GOPATH set properly)?

If you at any point installed the package in `GOROOT` (either by having no `GOPATH` set or by including `GOROOT` itself in `GOPATH`) then there might still be a directory in `$GOROOT` (which is always checked first) that is overriding your `GOPATH`. To verify, run `go list -f {{.Dir}} importpath` and if it reports a directory under `$GOPATH` try deleting that first.

### Still need help?

Visit us on IRC or ask on the mailing list. You will want to provide the output of the following commands, in addition to any errors you are getting:

#### Linux/darwin

```
go version
go env
env | grep GO
```

#### Windows

```
go version
go env
set | findstr GO
```
