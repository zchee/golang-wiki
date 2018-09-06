## Builders

Build configs (at the top) and host configs (bottom) are listed here:

https://farmer.golang.org/builders

A builder runs on a certain host type. (e.g. `linux-386-387` is a build type. It runs on `host-linux-kubestd`, a Kubernetes-based linux/amd64 host)

They come from the file https://github.com/golang/build/blob/master/dashboard/builders.go

For design details about the coordinator, see https://golang.org/s/builderplan

# How to set up a builder
  1. talk to golang-dev@ to get a builder host type & hash (they can get one from e.g. https://build-dot-golang-org.appspot.com/key?builder=host-foo-bar), and put that in ` ~/.gobuildkey` or `~/.gobuildkey-host-foo-bar` or the file pointed to by env var `$GO_BUILD_KEY_PATH`.
  1. `go get -u golang.org/x/build/cmd/buildlet`
  1. Run the buildlet in a loop or under systemd: `while true; do buildlet -coordinator=farmer.golang.org -reverse-type=host-foo-bar -reboot=false; done`
  1. Verify you can see the host registered at https://farmer.golang.org/#pools in the "Reverse pool machine detail" section and "Reverse pool summary".
  1. Add a builder type to https://github.com/golang/build/blob/master/dashboard/builders.go (see the `addBuilder` lines). Run tests. Send the CL.
  1. Have golang-dev deploy it.

## Old-style builders

Older-style builders are listed below. These builders are configured and run manually. The bug https://github.com/golang/go/issues/21191 tracks migrating the remaining ones over to the new system.

| **title** | **description** | **owner** | **notes** |
|:----------|:----------------|:----------|:----------|
| nacl-arm-cheney | Raspberry Pi 3 | @davecheney |           |
| openbsd-arm | SolidRun CuBox-i4Pro, ARM Cortex A9 R2 792 MHz, 2GB RAM | @4a6f656c - Joel Sing |           |
| plan9-arm | Raspberry Pi 3 Model B | @0intro - David du Colombier | Plan 9 from Bell Labs |
| plan9-amd64-9front | VM | @0intro - David du Colombier | 9front |

# Builder Requirements
  * internet connection (at least be able to access Google and https://build.golang.org)
  * preferably with two or more (V)CPUs, as at least one test (` sync/atomic ` requires ` runtime.NumCPU() > 1 ` to test more completely)
  * at least 512MiB of memory (1GB or more highly recommended. 512MB might need a small `GOGC` setting to avoid thrashing.)

# Restrictions
  * The combination of Ubuntu 11.10 or 12.04 OMAP4 kernel and pandaboard (ES) have proven unstable as builders. See [issue 4305](https://code.google.com/p/go/issues/detail?id=4305). Make sure you have updated to the latest available 12.04.2 release.

