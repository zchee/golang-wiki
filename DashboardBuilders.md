## Coordinator-managed builders

Builders that are managed by the coordinator (VMs running on GCE or reverse buildlets, such as the new OS X builders) are listed here:

http://farmer.golang.org/builders

For design details about the coordinator, see http://golang.org/s/builderplan


## Old-style builders

Older-style builders are listed below. These builders are configured and run manually. The goal is to migrate as many as possible over to the new system.

| **title** | **description** | **owner** | **notes** |
|:----------|:----------------|:----------|:----------|
| android-arm-crawshaw | Nexus 7 | crawshaw | Builder runs on attached desktop, uses adb |
| darwin-amd64 | 2011 Mac Mini, 2.4Ghz Core i5 | adg       | Mac OS X 10.6 (10K549) |
| darwin-386 | 2011 Mac Mini, 2.4Ghz Core i5 | adg       | Mac OS X 10.6 (10K549) |
| dragonfly-amd64 | ?               | Justin Sherrill | ?         |
| freebsd-arm-paulzhol | Cubiboard2 1Gb RAM dual-core Cortex-A7 (Allwiner A20) | Yuval Pavel Zholkover | FreeBSD 11 r299674 with NODEBUG kernel (w/o INVARIANTS, WITNESS, DEADLKRES) |
| linux-arm-luitvd | RaspberryPi     | Luit van Drongelen |           |
| linux-ppc64 | Power8E big endian | bradfitz, rsc  |           |
| linux-ppc64-minux | Gentoo on PowerMac G5 (dual 2.7GHz ppc970fx) | minux  | Disabled, Go doesn't support ppc970 anymore          |
| linux-mips64le-cherry | Gentoo on Loongson 2F 800MHz, 1GB DDR2 | cherry | builds sharded on three machines |
| linux-mips64le-stitch | Cavium Octeon II CN6880, 32-core @ 1GHz, 8GB RAM | Ed Swierk | Debian sid, no FPU |
| linux-mips64-minux | Gentoo on EdgeRouter Lite, 500MHz dual core MIPS64r2, 512MB | minux |           |    
| nacl-arm  | samsung chromebook | rsc       | running chrubuntu |
| nacl-arm-cheney | Raspberry Pi 3 | @davecheney |           |
| netbsd-386-minux | KVM             | minux |           |
| netbsd-amd64-bsiegert | EC2 m1.small VM | Benny Siegert | on Brad's work EC2 account |
| openbsd-arm | SolidRun CuBox-i4Pro, ARM Cortex A9 R2 792 MHz, 2GB RAM | Joel Sing |           |
| plan9-386-ducolombier | Intel Core 2 Quad Q8200 2.33 GHz, 6GB | David du Colombier | Plan 9 from Bell Labs |
| plan9-arm | Raspberry Pi 3 Model B | David du Colombier | Plan 9 from Bell Labs |
| plan9-amd64-9front | VM | David du Colombier | 9front |
| solaris-amd64-smartos | E5-1650 Xeon, 6C/12T | Daniel Malon | runs illumos (smartos zone); dfc, aram have full access |
| solaris-amd64-solaris11 | VM              | Dave Cheney | runs Solaris 11 |

# Builder Requirements
  * internet connection (at least be able to access Google and http://build.golang.org)
  * preferably with two or more (V)CPUs, as at least one test (` sync/atomic ` requires ` runtime.NumCPU() > 1 ` to test more completely)
  * at least 512MiB of memory (1GB or more highly recommended. 512MB might need a small `GOGC` setting to avoid thrashing.)

# Restrictions
  * The combination of Ubuntu 11.10 or 12.04 OMAP4 kernel and pandaboard (ES) have proven unstable as builders. See [issue 4305](https://code.google.com/p/go/issues/detail?id=4305). Make sure you have updated to the latest available 12.04.2 release.

# How to set up a builder
  1. obtain a hash from Go team members, and put that in ` ~/.gobuildkey `
  1. go get golang.org/x/build/cmd/builder
  1. builder YOUR\_BUILDER\_NAME

# Special notes
  * Please make sure you've installed root certificates and that it's accessible to Go programs. For example, on NetBSD, you will need to install ` security/mozilla-rootcerts `.
  * If your builder runs Unix, please install ` perl `, as tests for ` go.tools/cmd/vet ` need it.
  * Raise ` ulimit `s on Unix: thread count (` -r `), nofiles (` -n `, 1024 should be fine)