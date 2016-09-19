## Install package `golang`

The `golang` Debian package may have already made its way into your Ubuntu distribution. Try this:

```
sudo add-apt-repository ppa:ubuntu-lxc/lxd-stable
sudo apt-get update
sudo apt-get install golang
```

Note there is golang in Ubuntu but it is not up to date. An up-to-date version may be found at 
https://launchpad.net/~ubuntu-lxc/+archive/ubuntu/lxd-stable

That is all you need to get `go` working on your system. (You can use `go env GOROOT` to be sure where the Go files are, if you're curious.) Don't forget to create your GOPATH.


## If that didn't work

See http://blog.labix.org/2013/06/15/in-flight-deb-packages-of-go
