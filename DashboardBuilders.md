# Introduction

This page lists details of the various builders assigned to the build.golang.org CI system

## New-style Builders

See http://golang.org/s/builderplan

| **title** | **description** | **owner** | **notes** |
|:----------|:----------------|:----------|:----------|
| linux-386 | in Docker on GCE | bradfitz  |           |
| linux-386-387 | in Docker on GCE | bradfitz  | GO386=387 |
| linux-386-clang | in Docker on GCE | bradfitz  | Debian wheezy + clang 3.5 instead of gcc |
| linux-386-sid | in Docker on GCE | bradfitz  | Debian sid |
| linux-amd64 | in Docker on GCE | bradfitz  |           |
| linux-amd64-clang | in Docker on GCE | bradfitz  | Debian wheezy + clang 3.5 instead of gcc |
| linux-amd64-nocgo | in Docker on GCE | bradfitz  | cgo disabled |
| linux-amd64-noopt | in Docker on GCE | bradfitz  | optimizations and inlining disabled |
| linux-amd64-race| in Docker on GCE | bradfitz  |           |
| linux-amd64-sid | in Docker on GCE | bradfitz  | Debian sid |
| nacl-386  | in Docker on GCE | bradfitz  |           |
| nacl-amd64p32 | in Docker on GCE | bradfitz  |           |
| openbsd-amd64-gce56 | in VM on GCE | bradfitz  | Using buildlet; OpenBSD 5.6; GCE VM is built from script in tools/dashboard/env/openbsd-amd64         |

## Legacy Builders

These builders are configured and run manually. The goal is to migrate as many as possible over to the new system.

| **title** | **description** | **owner** | **notes** |
|:----------|:----------------|:----------|:----------|
| darwin-amd64 | 2011 Mac Mini, 2.4Ghz Core i5 | adg       | Mac OS X 10.6 (10K549) |
| darwin-amd64-cheney | 2011 Mac Mini, 2.4Ghz Core i5 | Dave Cheney | Mac OS X 10.10 XCode 5 |
| darwin-amd64-race-cheney | 2011 Mac Mini, 2.4Ghz Core i5 | Dave Cheney | Mac OS X 10.10 XCode 5 |
| darwin-386 | 2011 Mac Mini, 2.4Ghz Core i5 | adg       | Mac OS X 10.6 (10K549) |
| darwin-386-cheney | 2011 Mac Mini, 2.4Ghz Core i5  | Dave Cheney | Mac OS X 10.10 XCode 5 |
| dragonfly-amd64 | ?               | Justin Sherrill | ?         |
| dragonfly-386 | ?               | Justin Sherrill | ?         |
| freebsd-386 | rootbsd.net VPS | adg       | FreeBSD 9.1 |
| freebsd-amd64 | rootbsd.net VPS | adg       | FreeBSD 9.1 |
| freebsd-amd64-race | rootbsd.net VPS | adg       | FreeBSD 9.2, Only runs -race tests (./race.bash) |
| linux-arm-luitvd | RaspberryPi     | Luit van Drongelen |           |
| linux-arm-arm5 | QNAP TS-119P, ARMv5 @ 2.0GHz, 512MB | Dave Cheney | GOARM=5   |
| linux-arm-cheney-imx6 | Solidrun Cubox-i, quad core Cortex-A9 ~ 1Ghz, 2Gb ram | Dave Cheney | Runs arch linux, iMX6 boards need 3.10.x or above to pass the build reliably |
| nacl-arm  | samsung chromebook | rsc       | running chrubuntu |
| nacl-arm-cheney | same builder as linux-arm-cheney-imx6 | Dave Cheney |           |
| openbsd-386-rootbsd | VM on RootBSD   | adg/jsing       | OpenBSD 5.6 |
| openbsd-386-crawshaw | VM              | crawshaw  | OpenBSD 5.5 |
| openbsd-amd64-rootbsd | VM on RootBSD   | adg/jsing       | OpenBSD 5.6 |
| netbsd-386-minux | KVM             | Shenghou Ma |           |
| netbsd-amd64-bsiegert | EC2 m1.small VM | Benny Siegert | on Brad's work EC2 account |
| plan9-386-cnielsen | Intel Core 2 Quad Q8200 2.33 GHz, 6GB | David du Colombier | Plan 9 from Bell Labs, updated nightly |
| plan9-amd64-aram | VM              | Nick Owens  | runs 9front |
| solaris-amd64-smartos | E5-1650 Xeon, 6C/12T | Daniel Malon | runs illumos (smartos zone); dfc, aram have full access |
| solaris-amd64-solaris11 | VM              | Dave Cheney | runs Solaris 11 |
| windows-386 | on GCE 16 core instance, same machine as windows-amd64 | bradfitz  |           |
| windows-amd64 | on GCE 16 core instance, same machine as windows-386 | bradfitz  |           |
| windows-amd64-race | Windows 8.1, 2 x Intel Xeon E5620 @ 2.4GHz, 8 HT cores, 12GB RAM | Dmitry Vyukov | Only runs -race tests (./race.bash) |

# Builder Requirements
  * internet connection (at least be able to access Google and http://build.golang.org)
  * preferably with two or more (V)CPUs, as at least one test (` sync/atomic ` requires ` runtime.NumCPU() > 1 ` to test more completely)
  * at least 512MiB of memory

# Restrictions
  * The combination of Ubuntu 11.10 or 12.04 OMAP4 kernel and pandaboard (ES) have proven unstable as builders. See [issue 4305](https://code.google.com/p/go/issues/detail?id=4305). Make sure you have updated to the latest available 12.04.2 release.

# How to set up a builder
  1. obtain a hash from Go team members, and put that in ` ~/.gobuildkey `
  1. go get golang.org/x/tools/dashboard/builder
  1. builder YOUR\_BUILDER\_NAME

# Special notes
  * Please make sure you've installed root certificates and it's accessible to Go programs. For example, on NetBSD, you will need to install ` security/mozilla-rootcerts `.
  * If your builder runs Unix, please install ` perl `, as tests for ` go.tools/cmd/vet ` need it.
  * Use ` screen(1) ` instead of ` tmux(1) ` to host the ` builder ` process, as the later interference with some of the ` os/signal ` tests.
  * Raise ` ulimit `s on Unix: thread count (` -r `), nofiles (` -n `, 1024 should be fine)