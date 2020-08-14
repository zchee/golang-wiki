> The Go project's official download page is at [https://golang.org/dl](https://golang.org/dl/).
>
> After downloading a binary release suitable for your system, you can install go by following  the official installation instructions at [https://golang.org/doc/install](https://golang.org/doc/install#install).

There are some other options for Debian based systems like Ubuntu. These packages were not created by the Go project, and we don't support them, but they may be useful for you.

If you're using Ubuntu 18.04 LTS or 20.04 LTS on amd64, arm64, armhf or i386, then you can use the [longsleep/golang-backports PPA](https://launchpad.net/~longsleep/+archive/ubuntu/golang-backports) and update to Go 1.15.

```
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt update
sudo apt install golang-go
```

> **Note that `golang-go` installs latest Go as default Go. If you do not want that, install `golang-1.15` instead and use the binaries from `/usr/lib/go-1.15/bin`.**

If that's too new for you, try: (Ubuntu 19.04 max)

```
$ sudo add-apt-repository ppa:gophers/archive
$ sudo apt update
$ sudo apt install golang-1.11-go
```

> **Note that `golang-1.11-go` puts binaries in `/usr/lib/go-1.11/bin`. If you want them on your PATH, you need to make that change yourself.**

Using [snaps](https://snapcraft.io/go) also works quite well:

```
$ sudo snap install --classic go
```
> A restart may or may not be required for the command to be recognized depending on your system.

Using [getgo](https://github.com/golang/tools/tree/master/cmd/getgo) (proof-of-concept command-line installer for Go):

```
curl -LO https://get.golang.org/$(uname)/go_installer && chmod +x go_installer && ./go_installer && rm go_installer
```
> Getgo will install the Go distribution (tools & stdlib) to "/.go" inside your home directory.
