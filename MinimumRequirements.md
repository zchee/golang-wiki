# Minimum Requirements

## Operating Systems

### [Linux](Linux)

Kernel version 2.6.23 or later. [_This depends on architecture though, we need to have specific builder for this._] Linux/ARMv5 requires much newer kernels, at least v3.1 (for `__kuser_cmpxchg64`).

We don't support CentOS 5. Kernel is too old (2.6.18).

For little-endian MIPS64, kernel version [4.1 is known to fail, and 4.8 works](https://golang.org/issue/16848). 

### Windows

Windows XP (w/ Service Pack 2) or higher. But we don't currently (2016-09-23) have a Windows XP running. That is https://github.com/golang/go/issues/10267

We run builders testing Go on Windows Server 2008 R2 Datacenter Edition. That is basically Windows 7 or above.

### [macOS (née OS X, aka Darwin)](Darwin)

macOS Sierra (10.12) requires Go 1.7.1. We have not yet (as of 2016-09-23) backported the time system call fixes to any earlier Go versions. See https://github.com/golang/go/issues/16352.

Go only supports OS X 10.8 (Mountain Lion) or newer. We only have builders for 10.8, 10.10, and 10.11 as of 2016-09-23.

Go tip doesn't compile on OS X 10.7 (Lion) but binaries MAY work there. Maybe. No builders, no promises. We don't recommend it.

OS X 10.6 (Snow Leopard) is explicitly unsupported. See https://github.com/golang/go/issues/9511

### [OpenBSD](OpenBSD)

The current officially supported -stable versions only. See https://golang.org/wiki/OpenBSD for details.

### [DragonFly BSD](DragonFly-BSD)

Generally only the latest release version only. We have a builder, but it's not the most stable of our ports.

### [FreeBSD](FreeBSD)

FreeBSD 8 and up according to https://golang.org/doc/install, but I suspect we might need something newer than 8. We only run builders testing FreeBSD 10.1 and 11.0.

### [Native Client](NativeClient)

pepper_39 or newer.

### [Solaris](Solaris)

illumos (former OpenSolaris 10) based distributions or Oracle Solaris 11+. 

## Architectures

### amd64

All 64-bit x86 processors.

### 386

See https://golang.org/doc/install/source#environment

* GO386=387: run on any Pentium MMX or later processor.
* GO386=sse2: run on any processor with at least SSE2 (the default).

### arm

See https://golang.org/doc/install/source#environment

* GOARM=5: use software floating point; when CPU doesn't have VFP co-processor
* GOARM=6: use VFPv1 only; default if cross compiling; usually ARM11 or better cores (VFPv2 or better is also supported)
* GOARM=7: use VFPv3; usually Cortex-A cores

### arm64

All ARMv8-A processors.

### ppc64 (big endian)

POWER5 and above.
Starting with Go 1.9, only POWER8 and above are supported.

### ppc64le (little endian)

POWER8 and above.

### mips64 (big endian)

MIPS III or higher. Builder is using MIPS64r2.

### mips64le (little endian)

MIPS III or higher in little endian mode. Builders are using Loongson 2E/2F.

### s390x

z196+

### mips (big endian) and mipsle (little endian)

MIPS32r1, with FPU or kernel FPU emulation