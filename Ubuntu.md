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

Using the GVM for installation and compile natively.

## compile native
http://www.hostingadvice.com/how-to/install-golang-on-ubuntu/

## How to uninstall from the apt manager Uninstall just golang-go from [Universe](http://installion.co.uk/ubuntu/vivid/universe/index.html)

### This will remove just the golang-go package itself.
`sudo apt-get remove golang-go`

### Uninstall golang-go and its dependencies
`sudo apt-get remove --auto-remove golang-go`

### Purging your config/data too
`sudo apt-get purge golang-go` or `sudo apt-get purge --auto-remove golang-go`

### install for 1.7.1
I recommend to check out this [note](http://www.itzgeek.com/how-tos/linux/centos-how-tos/install-go-1-7-ubuntu-16-04-14-04-centos-7-fedora-24.html).

### Download the package Go 1.8
`wget https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz`
### extract the package
`sudo tar -zxvf  go1.8.linux-amd64.tar.gz -C /usr/local/`
### Added by Go Path

```
echo 'export GOROOT=/usr/local/go' >> ~/.bashrc
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> ~/.bashrc
```