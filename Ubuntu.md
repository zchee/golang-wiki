> The Go project's official download page is at [https://golang.org/dl](https://golang.org/dl/).
>
> After downloading a binary release suitable for your system, you can install go by following  the official installation instructions at [https://golang.org/doc/install](https://golang.org/doc/install#install).

There are some other options for Debian based systems like Ubuntu.  These packages were not created by the Go project, and we don't support them, but they may be useful for you.

If you're using Ubuntu 18.04 LTS or 19.10 on amd64, arm64, armhf or i386, then you can use the `longsleep/golang-backports` PPA and install Go 1.14.

```
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt update
sudo apt install golang-go
```

> **Note that `golang-go` installs latest Go as default Go. If you do not want that, install `golang-1.14` instead and use the binaries from `/usr/lib/go-1.14/bin`.**

If that's too new for you, try: (ubuntu 19.04 max, 19.10 not supported)

```
$ sudo add-apt-repository ppa:gophers/archive
$ sudo apt update
$ sudo apt install golang-1.11-go
```

> **Note that `golang-1.11-go` puts binaries in `/usr/lib/go-1.11/bin`. If you want them on your PATH, you need to make that change yourself.**

Using [snaps](https://snapcraft.io/go) also works quite well: (go1.14.1)

```
# This will give you the latest version of go
$ sudo snap install --classic go
```
> A restart may or may not be required for the command to be recognized depending on your system.

Using Google's Installer:
--
    cd ~
    curl -O https://storage.googleapis.com/golang/getgo/installer_linux
    chmod 700 installer_linux
    ./installer_linux
    mv .go /usr/local/go

