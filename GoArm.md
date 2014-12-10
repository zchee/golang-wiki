# Introduction

Go is fully supported on linux/arm. Any Go program that you can compile for x86/x86\_64 should work on Arm.

# Supported architectures

Go supports the following ARM architectural families.

| **Architecture** | **Status** | **GOARM value** | **Notes** |
|:-----------------|:-----------|:----------------|:----------|
| ARMv4 and below  | sorry, not supported | n/a             |           |
| ARMv5            | supported  | GOARM=5         |           |
| ARMv6            | supported  |                 | GOARM=6 is the default value|
| ARMv7            | supported  | GOARM=7         |           |
| ARMv8            | work in progress | n/a             | contact aram for details |

Starting from Go 1.1, the appropriate GOARM value will be chosen if you compile Go from source on the target machine. In cross compilation situations, it is recommended that you always export an appropriate GOARM value.

# Supported operating systems

Go supports ARM on Linux. You must be running a [EABI](http://wiki.debian.org/ArmEabiPort) kernel. These are generally known as ` armel ` for softfloat (compatible with ARMv5) or ` armhf ` for hardware floating point (ARMv6 and above).

# Recommended Go version

The recommended minimum version for running Go on arm systems is Go 1.1.

# Tips and tricks

## /tmp and tmpfs
The ` go ` build tool uses ` /tmp ` when compiling and testing, this can cause heavy wear and tear if ` /tmp ` lives on your SD card. To minimise this effect, either ` export TMPDIR ` to somewhere that lives on another filesystem. Alternatively if you have lots of physical memory you can mount a swap backed tmpfs filesystem on /tmp by adding this line to ` /etc/fstab `

```
tmpfs /tmp tmpfs nodev,nosuid,mode=1777 0 0
```

## Swap
Building Go from source requires at least 256mb of RAM. Running the tests requires at least 256mb of memory and at least 512mb of swap space.

## Build failures due to lack of memory
The Go tool will try to keep all your cpu cores busy when installing packages (during make.bash),
this is normally preferable on PCs where memory is abundant.
However, some powerful multicore ARM machines don't have enough memory to support parallel
builds utilizing all available cores, and you can work around that by using the ` taskset(1) ` utility
to limit Go to only use one core without resorting to swaps.
```
taskset 1 ./make.bash # use 3 if you want to use two cores
```
Note: the 1 here is a bitmask for cpu affinity and it's not the number of cpu cores you're
willing to use, please refer to ` taskset(1) ` manual for details.

# Known issues

## Lack of floating point hardware on ARMv5
The major issue with ARMv5 is the lack of floating point support in common ARMv5 harware<sup>†</sup>. When compiled with the GOARM=5 environment variable, the 5l linker will insert a call to ` _sfloat ` before any block of floating point instructions to branch into the floating point emulator. This means that binaries produced with a Go installation that was compiled with soft float support will work on all supported architectures, but builds compiled without soft floating point support will not work on ARMv5.

<sup>†</sup> This isn't strictly true, there exist ARMv5 implementations which have VFP1 floating point. However the compiler doesn't support VFP1 yet.

## html/template and test/nilptr.go test fail on HTC Android
html/template test and test/nilptr.go is known to fail on HTC's Android kernels ([ref](http://www.mail-archive.com/android-developers@googlegroups.com/msg153389.html)), because the kernel will kill  the application after 10 segfaults.

## Potential kernel bug in 2.6.32-5-kirkwood on QNAP 219P
See [Issue 5466](https://code.google.com/p/go/issues/detail?id=5466) for details. Updating to 3.2.0-4-kirkwood solved the issue.

# Success stories

ARM hardware comes in a myriad of shapes and sizes. If you've had a success story building and running Go on your Arm system, please detail your results here.

## Netgear Stora

Architecture: ARMv5

Operating System: Debian Sid

The Netgear Stora is an ARMv5 (Marvell Kirkwood) platform. I flashed mine with a Debian Sid distribution and it was, until Go1, a solid platform for Go development. The main drawback is the Stora only has 128mb of ram, which is not quite enough to run ./all.bash as 5l can use more than 100mb of ram when linking some commands.

Instructions for installing Debian on your Stora can be found on the OpenStora website, http://www.openstora.com/wiki/index.php?title=How_to_install_Debian_Linux_on_NETGEAR_Stora.

> _-- dave cheney_

## Qnap TS-119P II

Architecture: ARMv5

Operating System: Debian Squeeze

The Qnap TS series of NASs are excellent hackable little linux hosts. The TS-11P9 II is a 2Ghz Marvell Kirkwood ARMv5 processor with 512mb of ram and a single SATA drive bay.

The kirkwood platform is supported by the native debian installer. http://www.cyrius.com/debian/kirkwood/qnap/ts-119/install.html

> _-- dave cheney_

## Pandaboard

Architecture: ARMv7

Operating System: Ubuntu 12.04LTS (armhf)

The Pandaboard is a dual core ARMv7 development board based on the Texas Instruments OMAP4 SoC platform. I run ubuntu 12.04 LTS server on mine, which is an excellent distribution for Arm development. The Pandaboard has a gig of ram which makes it excellent for development and benchmarking.

Instructions and SD card image can be found on on the Ubuntu wiki, https://wiki.ubuntu.com/ARM/Server/Install#Installing_pre-installed_OMAP4_Precise_.2812.04.29_Server_Images.

> _-- dave cheney_

## BeagleBone

Architecture: ARMv7 single core, Cortex-A8, 256MB RAM, 720 MHz

Operating System: Angstrom Linux

BeagleBone is similar to Beagleboard, but without the video components. Angstrom is a very small Linux distribution for ARM based systems. It is built on top of Yocto and OpenEmbedded with additional tools and recipes to make it even easier to build a distribution. You can think of Angstrom as Ubuntu and OpenEmbedded/Yocto as Debian. Angstrom is very light weight and fast compared to Ubuntu. It uses systemd instead of the sys5 scripts which help give you a very fast boot time of a few seconds.

BeagleBone is probably faster than a RasberryPI because of it's newer Cortex-A8 dual-issue superscalar architecture, but the PI has the GPU which theoretically could be used with something like OpenCL to really run circles around the BeagleBone. However, for embedded applications the BeagleBone is easier to work with because it is ready out of the box with GPIO connections.

I've cross compiled for ARM with 5g from a Mac and so far I haven't run into any problems. You can build on the BeagleBone, but cross compiling with Go is so easy that it is better to save wear and tear on the flash drive and just compile somewhere else.

> _-- hans stimer_

### Zyxel NSA 310

Architecture: ARM5
Platform: Debian Wheeze

Successfuly built default branch, going to write fan control daemon for this device in golang.

### Raspberry Pi

Architecture: ARM1176JZFS, with floating point, running at 700Mhz

Operating System: Debian Wheezy beta distribution (http://www.raspberrypi.org/archives/1435) reported as:

` Linux raspberrypi 3.1.9+ #125 PREEMPT Sun Jun 17 16:09:36 BST 2012 armv6l GNU/Linux `

**Memory Split**: the Pi shares its 256mb of memory between the CPU and the GPU. You should allocate as much memory as possible to the CPU for a successful compilation. The configuration for the memory split is stored on your SD card. This link has a script to adjust the configuration, http://sirlagz.net/?p=445.

Go version weekly.2012-03-27 +645947213cac, with timeout and GOARM 7 patches http://codereview.appspot.com/5987063/) builds with 2 test failures: encoding/gob fails with out of memory, and fmt fails the NaN test.

Successfully installed and run SVGo via go get github.com/ajstarks/svgo, tested with goplay:

![http://farm8.staticflickr.com/7139/7451061716_fbb585c55f.jpg](http://farm8.staticflickr.com/7139/7451061716_fbb585c55f.jpg)

Division benchmark via http://codereview.appspot.com/6258067:


```
$ cd $GOROOT/src/pkg/runtime
$ go test -test.bench=BenchmarkUint


BenchmarkUint32Div7	 5000000	       547 ns/op
BenchmarkUint32Div37	 5000000	       547 ns/op
BenchmarkUint32Div123	 5000000	       547 ns/op
BenchmarkUint32Div763	 5000000	       547 ns/op
BenchmarkUint32Div1247	 5000000	       547 ns/op
BenchmarkUint32Div9305	 5000000	       547 ns/op
BenchmarkUint32Div13307	 5000000	       547 ns/op
BenchmarkUint32Div52513	 5000000	       547 ns/op
BenchmarkUint32Div60978747	 5000000	       547 ns/op
BenchmarkUint32Div106956295	 5000000	       547 ns/op
BenchmarkUint32Mod7	 5000000	       547 ns/op
BenchmarkUint32Mod37	 5000000	       547 ns/op
BenchmarkUint32Mod123	 5000000	       547 ns/op
BenchmarkUint32Mod763	 5000000	       547 ns/op
BenchmarkUint32Mod1247	 5000000	       547 ns/op
BenchmarkUint32Mod9305	 5000000	       547 ns/op
BenchmarkUint32Mod13307	 5000000	       547 ns/op
BenchmarkUint32Mod52513	 5000000	       547 ns/op
BenchmarkUint32Mod60978747	 5000000	       547 ns/op
BenchmarkUint32Mod106956295	 5000000	       547 ns/op
```

Running the hardware floating point distribution, Raspbian "pisces" (http://www.raspbian.org/PiscesImages) and applying the patches in https://gist.github.com/3116118, here are the results of the Eleanor McHugh gospeed benchmark:

```
raspbian@pisces:~/gowork/src/github.com/feyeleanor/gospeed$ uname -a
Linux pisces 3.1.9+ #171 PREEMPT Tue Jul 17 01:08:22 BST 2012 armv6l GNU/Linux
raspbian@pisces:~/gowork/src/github.com/feyeleanor/gospeed$ go test -test.bench=".*"
PASS
BenchmarkBaselineCastInt32ToInt	100000000	        13.5 ns/op
BenchmarkBaselineCastIntToInt32	100000000	        13.5 ns/op
BenchmarkBaselineCastInt64ToUint64	100000000	        17.8 ns/op
BenchmarkBaselineCastUint64ToInt64	100000000	        17.2 ns/op
BenchmarkBaselineVariableGet	100000000	        13.4 ns/op
BenchmarkBaselineVariableSet	100000000	        22.4 ns/op
BenchmarkBaselineVariableGetInterface	100000000	        13.5 ns/op
BenchmarkBaselineVariableSetInterface	50000000	        31.3 ns/op
BenchmarkBaselineVariableIncrement	100000000	        23.9 ns/op
BenchmarkBaselineVariableDecrement	100000000	        23.9 ns/op
BenchmarkBaselineFieldGet	100000000	        13.5 ns/op
BenchmarkBaselineFieldSet	100000000	        20.9 ns/op
BenchmarkBaselineSliceGet	50000000	        32.9 ns/op
BenchmarkBaselineSliceSet	50000000	        34.5 ns/op
BenchmarkBaselineMapIntGet	 1000000	      1448 ns/op
BenchmarkBaselineMapIntSet	 1000000	      1968 ns/op
BenchmarkBaselineMapStringGet	 1000000	      1119 ns/op
BenchmarkBaselineMapStringSet	 1000000	      1675 ns/op
BenchmarkBaselineIf	100000000	        15.0 ns/op
BenchmarkBaselineIfElse	100000000	        15.0 ns/op
BenchmarkBaselineSwitchDefault	100000000	        13.5 ns/op
BenchmarkBaselineSwitchOneCase	100000000	        15.0 ns/op
BenchmarkBaselineSwitchTwoCases	100000000	        18.0 ns/op
BenchmarkBaselineSwitchTwoCasesFallthrough	100000000	        18.0 ns/op
BenchmarkBaselineForLoopIteration	50000000	        42.0 ns/op
BenchmarkBaselineForReverseLoopIteration	50000000	        36.0 ns/op
BenchmarkBaselineForRange	20000000	        80.9 ns/op
BenchmarkBaselineForSliceLength	50000000	        39.0 ns/op
BenchmarkBaselineForReverseSliceLength	50000000	        36.0 ns/op
BenchmarkBaselineForLoopIteration10	20000000	       119 ns/op
BenchmarkBaselineForReverseLoopIteration10	20000000	        92.9 ns/op
BenchmarkBaselineForRange10	10000000	       215 ns/op
BenchmarkBaselineForSliceLength10	20000000	       109 ns/op
BenchmarkBaselineForReverseSliceLength10	20000000	        92.9 ns/op
BenchmarkBaselineForLoopIteration100	 2000000	       929 ns/op
BenchmarkBaselineForReverseLoopIteration100	 5000000	       700 ns/op
BenchmarkBaselineForRange100	 1000000	      1567 ns/op
BenchmarkBaselineForSliceLength100	 2000000	       853 ns/op
BenchmarkBaselineForReverseSliceLength100	 5000000	       700 ns/op
BenchmarkBaselineForLoopIteration10000	   10000	    106006 ns/op
BenchmarkBaselineForReverseLoopIteration10000	   50000	     67480 ns/op
BenchmarkBaselineForRange10000	   10000	    153841 ns/op
BenchmarkBaselineForSliceLength10000	   20000	     85735 ns/op
BenchmarkBaselineForReverseSliceLength10000	   50000	     69461 ns/op
BenchmarkBaselineMakeChannelBoolUnbuffered	  200000	     10162 ns/op
BenchmarkBaselineMakeChannelBool1	  200000	     12517 ns/op
BenchmarkBaselineMakeChannelBool10	  200000	     12521 ns/op
BenchmarkBaselineMakeChannelStringUnbuffered	  500000	     10369 ns/op
BenchmarkBaselineMakeChannelString1	  200000	     12576 ns/op
BenchmarkBaselineMakeChannelString10	  100000	     22358 ns/op
BenchmarkBaselineGo	   50000	    367593 ns/op
BenchmarkBaselineFunctionCall	50000000	        57.0 ns/op
BenchmarkBaselineFunctionCallArg	20000000	        81.0 ns/op
BenchmarkBaselineFunctionCall5VarArgs	  500000	      6852 ns/op
BenchmarkBaselineFunctionCallInt	50000000	        60.3 ns/op
BenchmarkBaselineFunctionCall5VarInts	 1000000	      3185 ns/op
BenchmarkBaselineFunctionCallWithDefer	 1000000	      2330 ns/op
BenchmarkBaselineFunctionCallPanicRecover	  500000	      6222 ns/op
BenchmarkBaselineMethodCallDirect	20000000	        83.8 ns/op
BenchmarkBaselineMethodCallDirect1Arg	20000000	       106 ns/op
BenchmarkBaselineMethodCallDirect1Int	20000000	        85.2 ns/op
BenchmarkBaselineMethodCallDirect5Args	 5000000	       368 ns/op
BenchmarkBaselineMethodCallDirect5Ints	10000000	       233 ns/op
BenchmarkBaselineMethodCallIndirect	100000000	        18.0 ns/op
BenchmarkBaselineMethodCallIndirect1Arg	50000000	        42.0 ns/op
BenchmarkBaselineMethodCallIndirect1Int	100000000	        19.5 ns/op
BenchmarkBaselineMethodCallIndirect5Args	 5000000	       309 ns/op
BenchmarkBaselineMethodCallIndirect5Ints	10000000	       168 ns/op
BenchmarkBaselineTypeAssertion	10000000	       218 ns/op
BenchmarkBaselineTypeAssertionEmptyInterface	20000000	       106 ns/op
BenchmarkBaselineTypeAssertionInterface1	 5000000	       576 ns/op
BenchmarkBaselineTypeAssertionInterface2	 5000000	       579 ns/op
BenchmarkBaselineTypeReflectPrimitiveToValue	 5000000	       425 ns/op
BenchmarkBaselineTypeReflectSliceToValue	 1000000	      3218 ns/op
BenchmarkBaselineTypeReflectStructToValue	  500000	      4760 ns/op
BenchmarkBaselineTypeCheck	10000000	       189 ns/op
BenchmarkBaselineTypeCheckEmptyInterface	20000000	        93.1 ns/op
BenchmarkBaselineTypeCheckInterface1	 5000000	       511 ns/op
BenchmarkBaselineTypeCheckInterface2	 5000000	       516 ns/op
BenchmarkBaselineTypeSwitchOneCase	10000000	       262 ns/op
BenchmarkBaselineTypeSwitchBasicTypesCase	10000000	       295 ns/op
BenchmarkBaselineTypeSwitchEmptyInterface	10000000	       163 ns/op
BenchmarkBaselineTypeSwitchInterface1	 5000000	       588 ns/op
BenchmarkBaselineTypeSwitchInterface2	 5000000	       602 ns/op
BenchmarkBaselineNewStructureLiteral	20000000	        84.0 ns/op
BenchmarkBaselineNewStructure	20000000	       127 ns/op
BenchmarkBaselineNewSliceLiteral	50000000	        54.2 ns/op
BenchmarkBaselineNewSlice	 1000000	      3124 ns/op
BenchmarkBaselineNewMapLiteralIntToInt	  500000	      9083 ns/op
BenchmarkBaselineNewMapLiteralIntToInterface	  500000	      9807 ns/op
BenchmarkBaselineNewMapLiteralStringToInt	  500000	      9792 ns/op
BenchmarkBaselineNewMapLiteralStringToInterface	  500000	     10595 ns/op
BenchmarkBaselineNewMapLiteralIntToInt2Item	  200000	     14265 ns/op
BenchmarkBaselineNewMapLiteralIntToInterface2Item	  200000	     14669 ns/op
BenchmarkBaselineNewMapLiteralStringToInt2Item	  200000	     14025 ns/op
BenchmarkBaselineNewMapLiteralStringToInterface2Item	  200000	     15086 ns/op
BenchmarkBaselineNewMapIntToInt	  500000	      9025 ns/op
BenchmarkBaselineNewMapIntToInterface	  500000	      9753 ns/op
BenchmarkBaselineNewMapStringToInt	  500000	      9740 ns/op
BenchmarkBaselineNewMapStringToInterface	  500000	     10486 ns/op
BenchmarkBaselineSliceCopy	 5000000	       300 ns/op
BenchmarkBaselineNewSliceAppendElement1	 1000000	      3318 ns/op
BenchmarkBaselineNewSliceAppendElement10	 1000000	      5174 ns/op
ok  	github.com/feyeleanor/gospeed	417.296s
```

_-- anthony starks_

## ODROID-X

Architecture: ARMv7 quad-core Cortex-A9 (Samsung Exynos 4412 1.4GHz), 1GB RAM, Mali graphics (untested).

Operating System: [Archlinux ARM](http://archlinuxarm.org/)

Go pre-1.1 compiles out of the box. The four cores make it particularly suited to Go multi-threaded programs. An ODROID-X2 is coming (Nov 2012) with more RAM.

_-- Rémy Oudompheng_

## BananaPi

[BananaPi](http://bananapi.org) has a few enhanced hardware components compare with Raspberry Pi.

| **Architecture** | **Comments** |
|:-----------------|:-------------|
| [Allwinner A20(ARM Cortex-A7 Dual-core, 1GHz, Mali400MP2 GPU)](http://www.allwinnertech.com/en/clq/processora/A20.html) | tbc          |
| eSATA            | No worry to wear out your root SD Card|
| Onboard Microphone | tbc          |
| 1G Etherenet     | tbc          |
| 1G RAM           | tbc          |
| Reset Switch     | To reset the board ?|
| Power Switch     | To power cycle the board ?|

```

root@bpi01:/data/go13/src# cat ./buildgo.bash
#!/bin/bash
# use 1 CPU to avoid out of memory compilation issue.
time taskset 2 ./make.bash

root@bpi01:/data/go13/src# ./buildgo.bash

<snipped>

Installed Go for linux/arm in /data/go1.3
Installed commands in /data/go1.3/bin

real    9m9.222s
user    8m18.960s
sys     0m40.920s
root@bpi01:/data/go1.3/src#
```

_--T.J. Yang_

## AppliedMicro X-Gene (ARMv8)

Architecture: ARMv8 (64-bit) 8-core, 2.4GHz, 16GB RAM

Operating System: Linux

The linux/arm64 Go port is not functional yet, but you can run the linux/arm port.

```
$ sudo apt-get install gcc-arm-linux-gnueabihf libc6-dev-armhf-cross
$ 
$ cd go/src && CC='arm-linux-gnueabihf-gcc -static' GO_DISTFLAGS=-s GOHOSTARCH=arm GOARM=7 CGO_ENABLED=0 ./make.bash
$ 
$ uname -a
Linux xgene 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:56 UTC 2014 aarch64 aarch64 aarch64 GNU/Linux
$ go version
go version devel +6a8045fd9da9 Wed Dec 03 18:33:35 2014 +0100 linux/arm
$ go env
GOARCH="arm"
GOBIN=""
GOCHAR="5"
GOEXE=""
GOHOSTARCH="arm"
GOHOSTOS="linux"
GOOS="linux"
GOPATH="/home/aram"
GORACE=""
GOROOT="/home/aram/go"
GOTOOLDIR="/home/aram/go/pkg/tool/linux_arm"
CC="arm-linux-gnueabihf-gcc"
GOGCCFLAGS="-static -fPIC -marm -pthread -fmessage-length=0"
CXX="g++"
CGO_ENABLED="1"
```

A static toolchain is required as arm64 Linux distributions don't ship the necessary 32-bit arm libraries (except in a sysroot). ` GO_DISTFLAGS=-s ` is not enough, ` CC='arm-linux-gnueabihf-gcc -static' ` is required to build a static dist tool.

_-- Aram Hăvărneanu_