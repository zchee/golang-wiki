# The Automatic (but unsupported) Way: [winstrap](https://github.com/golang/winstrap)

The winstrap tool is used by the Go project to turn a fresh Windows VM image into a Windows builder. It installs all necessary dependencies. It's sometimes out of date, though, as it's only updated when we need to update the Windows base image for the [Go continuous build](https://build.golang.org/).

To use winstrap, download the latest version of winstrap.exe from the [winstrap](https://github.com/golang/winstrap) page and run it.

It will download some installers to your desktop, which you should run. Just click through; all the defaults are fine.

Then it will check out Go and place it in c:\Users\\%USER%\goroot and build it.

That's it.

Note however that winstrap is not supported. It's considered an internal tool used for occasional setup of new Windows builder images and is not actively maintained until we need it ourselves.

# The Manual Way

## Install MinGW/MSYS

Download and save the latest version of the automated MinGW installer executable (` exe `) file from SourceForge.

http://sourceforge.net/projects/mingw/files/Automated%20MinGW%20Installer/mingw-get-inst/

Open and run the saved automated MinGW installer executable file, which is named ` mingw-get-inst-yyyymmdd.exe `, where ` yyyymmdd ` is the version date stamp. For example, ` mingw-get-inst-20110530.exe `.

The MinGW Setup Wizard window will open with the title "Setup - MinGW-Get". Except for the following, accept the setup defaults, unless it's necessary to change them.

For Repository Catalogues, check the Download latest repository catalogues button.

For Select Components, the MinGW Compiler Suite, the C Compiler box is automatically checked. Scroll down to the bottom of the list and check the MinGW Developer Toolkit box, which includes the MSYS Basic System.

For Ready to Install, review and verify the installation settings, which should look similar this:
```
    Installing:
        mingw-get
        pkginfo
        C Compiler
        MSYS Basic System
        MinGW Developer Toolkit 
    Downloading latest repository catalogues 
    Destination location:
        C:\MinGW 
```
When the installation settings are correct, Install.

The installation loads the package installation catalogues and downloads and installs the files. The installation may take some time, largely depending on the download speed.

The MSYS terminal window may be opened by opening and running the ` C:\MinGW\msys\1.0\msys.bat ` batch file.

## Build

```
git clone https://go.googlesource.com/go
cd go\src
all.bat
```

## 64-bit Notes

  1. Ensure you are able to compile a working 32-bit Go first.
  1. Grab the latest zip from http://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Automated%20Builds/ and extract it over the MinGW directory, so that for example the .exe files end up in the same location as the 32-bit ones.
  1. Replace ` gcc.exe ` and ` ar.exe ` with their 64-bit counterparts.
  1. Set ` GOARCH=amd64 ` and away you go!

