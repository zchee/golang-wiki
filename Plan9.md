# Introduction

An experimental port of [Go](https://golang.org) is available for the [Plan 9 from Bell Labs](https://9p.io/plan9) operating system.

# Supported architectures

The Plan 9 port of Go is available for the following architectures:

* 386
* amd64
* arm

# Supported kernels

The current Go distribution has been tested successfully on:

* [Plan 9 from Bell Labs](https://9p.io/plan9) (386 and arm) kernel
* [9front](http://9front.org) amd64 kernel
* Charles Forsyth's [9k](https://bitbucket.org/forsyth/plan9-9k) (amd64) kernel

# Requirements

Plan 9 requires a kernel providing the following system calls:

* tsemacquire (available since [2012-06-30](https://github.com/0intro/plan9/commit/bd0c9332d5b1da1371d03e8e0ad03de0d08e08c6))
* nsec (available since [2014-05-15](https://github.com/0intro/plan9/commit/6c1d8fd563a815cbbac06f61bdc1d0f6331c3d3b))

A fix to the pread system call is required, so pread will not update the channel offset when reading a file:

* [9-pread-offset](http://9legacy.org/9legacy/patch/9-pread-offset.diff)

The TCP connection control file must handle the "close" message to be able close a TCP connection gracefully, while waking up the readers:

* [9-tcp-close](http://9legacy.org/9legacy/patch/9-tcp-close.diff)

A fix to Fossil is required to increment Qid.vers after a wstat, so a truncate followed by a read will return the content of the new file instead of the cached content.

* [fossil-wstat-qid](http://9legacy.org/9legacy/patch/fossil-wstat-qid.diff)

You will need support for SHA-2 signatures in X.509 certificates, so you could download sources from repositories hosted on GoogleSource, GitHub and so on.

* [libsec-x509-sha2](http://9legacy.org/9legacy/patch/libsec-x509-sha2.diff)

If you're running Plan 9 on Raspberry Pi, you'll require the latest [bcm](https://9p.io/magic/webls?dir=/sources/contrib/miller/9/bcm) kernel from Richard Miller.

CA certificates for `crypto/x509` package needs to be installed at `/sys/lib/tls/ca.pem`. You can download it from `https://curl.haxx.se/ca/cacert.pem` or copy from another system.

# Installation

Since Go is written in Go, you may want to bootstrap Go with Go 1.4.3, which is the latest release of Go written in C.

However, since the Go 1.4 runtime wasn't mature enough on Plan 9, we recommend you to bootstrap from a more recent version of Go, using another operating system.

## Boostraping from Plan 9

First, install Go 1.4:

```
cd /tmp
git clone -b go1.4.3 https://go.googlesource.com/go go1.4
cd go1.4/src
hget http://9legacy.org/go/patch/syscall-exec.diff | ape/patch -p2
make.rc
```

The [syscall-exec](http://9legacy.org/go/patch/syscall-exec.diff) patch is required if you're running a machine with SMP enabled.
		
Then, set the `GOROOT_BOOTSTRAP` environment variable:

```
GOROOT_BOOTSTRAP=/tmp/go1.4
```

Finally, install the latest version of Go:

```
cd /tmp
git clone https://go.googlesource.com/go
cd go/src
all.rc
bind -a /tmp/go/bin /bin
```
Go is now ready to use.

## Bootstraping from another operating system

First, you must have installed Go on this operating system, following the [Go installation instructions](https://golang.org/doc/install).

Then, you can cross-compile a Go toolchain for Plan 9:

```
cd $GOROOT/src
GOOS=plan9 GOARCH=386 ./bootstrap.bash
```

Then, the bootstrap toolchain will be available in `../../go-plan9-386-bootstrap.tbz`.

Finally, you can extract this archive to your Plan 9 machine.

For example:

```
cd /tmp
tar xzf go-plan9-386-bootstrap.tbz
bind -a /tmp/go-plan9-386-bootstrap/bin /bin
```

Go is now ready to use.

You'll be able to use this installation of Go to bootstrap future Go releases, by setting the `GOROOT_BOOTSTRAP` environment variable:

```
GOROOT_BOOTSTRAP=/tmp/go-plan9-386-bootstrap
```

## Bootstraping from binaries

A [binary package](https://storage.googleapis.com/go-builder-data/gobootstrap-plan9-386.tar.gz) for plan9/386 is available.

This binary package is used to bootstrap Go on the plan9/386 builder.

```
cd /tmp
hget -o gobootstrap-plan9-386.tar.gz https://storage.googleapis.com/go-builder-data/gobootstrap-plan9-386.tar.gz
mkdir gobootstrap-plan9-386
cd  gobootstrap-plan9-386
tar xzf ../gobootstrap-plan9-386.tar.gz
```

You'll be able to use this binary package of Go to bootstrap Go, by setting the `GOROOT_BOOTSTRAP` environment variable:

```
GOROOT_BOOTSTRAP=/tmp/gobootstrap-plan9-386
```

# Git

Git is not available on Plan 9. However a [Git wrapper](http://9legacy.org/9legacy/tools/git) is available as a simple rc script. It includes everything you need to use the [go](https://golang.org/cmd/go) tool.

# Builders

Three Plan 9 builders are currently running and reporting the results to the [Go Dashboard](http://build.golang.org/):

* plan9-386 is running Plan 9 from Bell Labs (386 kernel) on Google Compute Engine (new-style builder)
* plan9-arm is running Plan 9 from Bell Labs (arm kernel) on a Raspberry Pi 3 (old-style builder)
* plan9-amd64-9front is running 9front (amd64 kernel) on a virtual machine (old-style builder)

# Status

The Plan 9 port of Go is considered experimental and is still a work-in-progress. There is a number of known issues available on the [Go issue tracker](https://golang.org/issues).

# Issues

Many issues are currently open on the [Go issue tracker](https://golang.org/issues) with the [OS-Plan9](https://github.com/golang/go/issues?q=is%3Aopen+is%3Aissue+label%3AOS-Plan9) label.

# Help

The Plan 9 port of Go is a community-driven port. Any help to improve the Go port on Plan 9 would be highly appreciated.

# Maintainer

Many people have contributed to the Plan 9 port of Go. Since December 2013, the Plan 9 port of Go is maintained by [David du Colombier](https://github.com/0intro).
