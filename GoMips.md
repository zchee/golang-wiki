# Introduction

Go programs can be cross-compiled e.g., on x86/x86\_64 build systems to run on MIPS target machines. 

# Supported architectures

Go supports the following MIPS architectural families. (Are there more?)

| **Architecture** | **Status** | **GOMIPS value** | **GOARCH value** |
|:-----------------|:-----------|:----------------|:-----------------|
| Big endian (e.g., ar71xx) | supported  | GOMIPS=softfloat| GOARCH=mips      |
| Little endian            | supported  | n/a             | GOARCH=mipsle    |

# Supported operating systems

* MIPS on Linux. Tested with an ar71xx based OpenWrt device.

# Recommended Go version

The tested version for running Go on MIPS systems is Go 1.13.

# Tips and tricks

## Building for ar71xx OpenWrt

This builds a Go program, strips unneeded strings and symbols to minimize its size, and compresses it to further minimize its size:

```
env GOOS=linux GOARCH=mips GOMIPS=softfloat  go build -trimpath -ldflags="-s -w" 'server.go'
upx -9 server
```

# Success stories

MIPS hardware comes in a myriad of shapes and sizes. If you've had a success story building and running Go on your Arm system, please detail your results here.

## D-Link DIR-505 Mobile Companion

Architecture: ar71xx

Operating System: OpenWrt

The D-Link DIR-505 Mobile Companion comes with an Atheros AR1311 processor, 8 MB flash and 64 MB RAM. This space is limited but allows us to load Go applications, e.g., from network into `/tmpfs` and execute them from there.

Further information about the device can be found at https://openwrt.org/toh/d-link/dir-505.

