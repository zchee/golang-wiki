# Minimum Requirements

## Operating Systems

### Linux

Kernel version 2.6.23 or later. [_This depends on architecture though, we need to have specific builder for this._]

We don't support CentOS 5. Kernel is too old (2.6.18).

### Windows

Windows XP or higher. But we don't currently (2016-09-23) have a Windows XP running. That is https://github.com/golang/go/issues/10267

We run builders testing Go on Windows Server 2008 R2 Datacenter Edition. That is basically Windows 7 or above.

### macOS (née OS X, aka Darwin)

macOS Sierra (10.12) requires Go 1.7. We have not yet (as of 2016-09-23) backported the time system call fixes to any earlier Go versions. See https://github.com/golang/go/issues/16352.

Go only supports OS X 10.8 (Snow Leopard) or newer. We only have builders for 10.8, 10.10, and 10.11 as of 2016-09-23.

Go tip doesn't compile OS X 10.7 but binaries MAY work there. Maybe. No builders, no promises. We don't recommend it.

OS X 10.6 is explicitly unsupported. See https://github.com/golang/go/issues/9511

### OpenBSD

The current officially supported -stable versions only.

### DragonFly

Generally only the latest release version only. We have a builder, but it's not the most stable of our ports.

### FreeBSD

FreeBSD 8 and up according to https://golang.org/doc/install, but I suspect we might need something newer than 8.

### Solaris

illumos (former OpenSolaris 10) based distributions or Oracle Solaris 11+. 

## Architectures

### x86

See https://golang.org/doc/install/source#environment

Set GO386=387 or GO386=sse2 for older processors.

### arm

See https://golang.org/doc/install/source#environment

* GOARM=5: use software floating point; when CPU doesn't have VFP co-processor
* GOARM=6: use VFPv1 only; default if cross compiling; usually ARM11 or better cores (VFPv2 or better is also supported)
* GOARM=7: use VFPv3; usually Cortex-A cores

### arm64

??

### ppc64 (big endian)

PPC 970 or newer.

### ppc64le (little endian)

POWER8+

### s390x

z196+
