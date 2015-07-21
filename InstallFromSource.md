# Introduction

This is a companion to http://golang.org/doc/install/source providing additional instructions for various operating systems.

## Install C tools

On OS X, a C compiler is bundled in the command line tools for
[Xcode](http://developer.apple.com/Xcode/),
and you don't need to install the whole Xcode to compile Go.
If you have already installed Xcode 4.3+, you can install command
line tools from the Components tab of the Downloads preferences panel.
In more recent versions of Xcode, you can use ` xcode-select --install `
command to install the command line tools without opening Xcode.
To verify you have a working compiler, just invoke ` gcc `
in a freshly created Terminal window, unless you see the
` "gcc: command not found" ` error, you are ready to go.

On Ubuntu/Debian, use ` sudo apt-get install gcc libc6-dev `.
If you want to build 32-bit binaries on a 64-bit system you'll also need the ` libc6-dev-i386 ` package.

On RedHat/Centos 6, use ` sudo yum install gcc glibc-devel `.
If you want to build 32-bit binaries on a 64-bit system you'll need both
` glibc-devel.i386 ` and ` glibc-devel.x86_64 ` packages.

On Windows, install ` gcc ` with
[TDM-GCC](http://tdm-gcc.tdragon.net/).
(Make sure you add its ` bin ` subdirectory to your ` PATH `.) Go does not support the Cygwin toolchain.

## Easy build from source

Use [dotsoftware](http://g14n.info/dotsoftware/) to build Go from source in few minutes, just copy and paste the following code in your terminal

```
# get latest .software
cd
git clone https://github.com/fibo/.software.git
# source it in your profile and in current session
[ -f ~/.bash_profile ] && grep 'source ~/.software/etc/profile' ~/.bash_profile || echo 'source  /.software/etc/profile' >> ~/.bash_profile && source ~/.software/etc/profile
# build Golang
.software_install Golang
# you are done!
```
