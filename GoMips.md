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

## Teltonika RUT955

Architecture: ar9344  

Operating System: RutOS (based on OpenWrt)

The Teltonika RUT955 has a Atheros Wasp MIPS 74Kc CPU running at 550 MHz with 16 MB flash 128 MB RAM. Inbuilt flash will be insufficient for most applications but a Micro SD or USB stick can be added (running application directly from SD was unreliable but copying to /tmpfs and running from there works OK). The inbuilt IO, GPS etc can be accessed via Modbus TCP and the RS232/RS485 ports worked without issue. Tested with Go 1.14.6 & 1.15.3 (GOARCH=mips, GOMIPS=softfloat).

Further information about the device can be found at https://teltonika-networks.com/product/rut955/.

## TP-Link Archer A6 WiFi Router

Architecture: ath79 (same hardware as ar71xx, but with native kernel support)

Operating System: OpenWrt

The TP-Link Archer A6 comes with an Atheros QCA9563 MIPS 24K classic processor, 16 MB flash, and 128 MB RAM. Flash storage is limited and no USB ports are available for storage expansion, so programs are loaded from the network into /tmpfs and executed.

Further information about the device can be found at https://openwrt.org/toh/hwdata/tp-link/tp-link_archer_a6_us_tw.

## Belkin F7D7302 WiFi Router

Architecture: mipsel_74kc

Operating System: DD-WRT

The Belkin F7D7302 comes with a Broadcom BCM4716 little-endian MIPS 74K classic processor, 8 MB flash, and 64 MB RAM. Flash storage is severely limited, but there is a USB port available so programs can be loaded onto a flash drive and executed.

Further information about the device can be found at https://openwrt.org/toh/belkin/f7d3302.

## AVM FRITZ!Box 7362 SL

System type: xRX200 rev 1.2 \
CPU model: MIPS 34Kc V5.6

Operating System: OpenWrt 21

Further information about the device can be found at https://openwrt.org/toh/avm/avm_7362_sl.