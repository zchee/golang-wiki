The Go project's official download page is at [https://golang.org/dl/](https://golang.org/dl/).

There are some other options for Debian based systems like Ubuntu.  These packages were not created by the Go project, and we don't support them, but they may be useful for you.

If you're using Ubuntu 16.04 LTS, 18.04 LTS or 19.04 on amd64, arm64, armhf or i386, then you can use the `longsleep/golang-backports` PPA and install Go 1.13.

```
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt-get update
sudo apt-get install golang-go
```

> **Note that `golang-go` installs latest Go as default Go. If you do not want that, install `golang-1.13` instead and use the binaries from `/usr/lib/go-1.13/bin`.**

If that's too new for you, try:

```
$ sudo add-apt-repository ppa:gophers/archive
$ sudo apt-get update
$ sudo apt-get install golang-1.11-go
```

> **Note that `golang-1.11-go` puts binaries in `/usr/lib/go-1.11/bin`. If you want them on your PATH, you need to make that change yourself.**

Using snaps also works quite well:

```
# This will give you the latest version of go
$ sudo snap install --classic go
```
> A restart is required for the command to be recognized.
