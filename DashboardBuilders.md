## Coordinator-managed builders

Builders that are managed by the coordinator (VMs running on GCE or reverse buildlets, such as the new OS X builders) are listed here:

http://farmer.golang.org/builders

For design details about the coordinator, see http://golang.org/s/builderplan


## Old-style builders

Older-style builders are listed below. These builders are configured and run manually. The goal is to migrate as many as possible over to the new system.

| **title** | **description** | **owner** | **notes** |
|:----------|:----------------|:----------|:----------|
| dragonfly-amd64 | ?               | @fupjack - Justin Sherrill | ?         |
| freebsd-arm-paulzhol | Cubiboard2 1Gb RAM dual-core Cortex-A7 (Allwiner A20) | @paulzhol - Yuval Pavel Zholkover | FreeBSD 11.1-RELEASE |
| nacl-arm-cheney | Raspberry Pi 3 | @davecheney |           |
| openbsd-arm | SolidRun CuBox-i4Pro, ARM Cortex A9 R2 792 MHz, 2GB RAM | @4a6f656c - Joel Sing |           |
| plan9-386-ducolombier | Intel Core 2 Quad Q8200 2.33 GHz, 6GB | @0intro - David du Colombier | Plan 9 from Bell Labs |
| plan9-arm | Raspberry Pi 3 Model B | @0intro - David du Colombier | Plan 9 from Bell Labs |
| plan9-amd64-9front | VM | @0intro - David du Colombier | 9front |

# Builder Requirements
  * internet connection (at least be able to access Google and http://build.golang.org)
  * preferably with two or more (V)CPUs, as at least one test (` sync/atomic ` requires ` runtime.NumCPU() > 1 ` to test more completely)
  * at least 512MiB of memory (1GB or more highly recommended. 512MB might need a small `GOGC` setting to avoid thrashing.)

# Restrictions
  * The combination of Ubuntu 11.10 or 12.04 OMAP4 kernel and pandaboard (ES) have proven unstable as builders. See [issue 4305](https://code.google.com/p/go/issues/detail?id=4305). Make sure you have updated to the latest available 12.04.2 release.

# How to set up a builder
  1. talk to golang-dev@ to get a builder host type & hash (they can get one from e.g. https://build-dot-golang-org.appspot.com/key?builder=host-foo-bar), and put that in ` ~/.gobuildkey` or `~/.gobuildkey-host-foo-bar` or the file pointed to be env var `$GO_BUILD_KEY_PATH`.
  1. go get golang.org/x/build/cmd/buildlet
  1. Run the buildlet in a loop or under systemd: `while true; do buildlet -coordinator=farmer.golang.org -reverse-type=host-foo-bar -reboot=false; done`
  1. Verify you can see the host registered at https://farmer.golang.org/#pools in the "Reverse pool machine detail" section and "Reverse pool summary".
  1. Add a builder type to https://github.com/golang/build/blob/master/dashboard/builders.go (see the `addBuilder` lines). Run tests. Send the CL.
  1. Have golang-dev deploy it.