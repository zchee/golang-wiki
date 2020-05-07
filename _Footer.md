<!-- DO NOT EDIT THIS FOOTER -->
<!-- This is a wiki. We trust you to be a good person. -->
Hello.
I would like to start with many thanks to Go Lang inventors. I have been developing software for 35 years, and I find Go - the most clever language of all times.

I am relatively new to Go, but I went through almost all Go tutorials by now.

The subject of my issue is - to reuse a local package in different local applications/packages. 
The purpose is to first play with the package using it in different apps, before pushing it to a module in Git repository.

I tried developing and publishing a module to Git, then "get"-ting it, and using it. This - works very well for me.
I also tried putting a target package in a subfolder under the calling go main package - and it works perfectly as well.

But when I try to import the target package into another package (which is not in the parent folder to target package) - I am getting "not in GOROOT" error message, even though the archive ".a" file for target package is generated and the target package is under GOPATH/src/.
The target package is within GOPATH:
S:\MiGo\mibGOPATH\src\mibpacks\mibpackeleven
GOPATH is set to: S:\MiGo\mibGOPATH

It looks to me that [build] is not finding the target package in GOPATH.

Here is my very simple example:  


==========
Target package

Location: S:\MiGo\mibGOPATH\src\mibpacks\mibpackeleven
mibpackeleven.go:

package mibpackeleven
func HiFrommibpackeleven() string {
	var returnedValue = "Hello from HiFrommibpackeleven()"
	return returnedValue
}

After:
>go mod init mibpackeleven
go.mod:
module mibpackeleven
go 1.14

After:
>go install mibpackeleven
Archive file is created:
S:\MiGo\mibGOPATH\pkg\windows_amd64\mibpacks\mibpackeleven.a

==========
Calling package:

Location: S:\MiGo\mibGOPATH\src\mi-code\modulesCall\callpeleven
callpeleven.go:
package main
import (
	"fmt"
	"mibpacks/mibpackeleven"
)
func main() {
	toPrint := mibpackeleven.HiFrommibpackeleven()
	fmt.Println(toPrint)
}

After:
>go mod init callpeleven
go.mod:
module callpeleven
go 1.14

At any of the following attempts:
>go run callpeleven.go
>go build callpeleven.go
>go install callpeleven
I am getting the following error:
callpeleven.go:5:2: package mibpacks/mibpackeleven is not in GOROOT
(S:\GoLang\src\mibpacks\mibpackeleven)


Here are the values of major Go env variables: 
GO111MODULE=on
GOBIN=S:\MiGo\mibGOPATH\bin
GOHOSTOS=windows
GOPATH=S:\MiGo\mibGOPATH
GOROOT=S:\GoLang

I truly appreciate your help.
Thanks in advance.

Sincerely, 
Michael Bugaevski
mikejm618@gmail.com 

