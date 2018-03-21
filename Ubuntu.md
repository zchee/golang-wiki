The Go project's official download page is at [https://golang.org/dl/](https://golang.org/dl/).

There are some other options for Debian based systems like Ubuntu.  These packages were not created by the Go project, and we don't support them, but they may be useful for you.

Try:

```
$ sudo apt-get install golang-go
```

If that's too old for you, try:

```
$ sudo add-apt-repository ppa:gophers/archive
$ sudo apt-get update
$ sudo apt-get install golang-1.10-go
```

> **Note that golang-1.10-go puts binaries in /usr/lib/go-1.10/bin. If you want them on your PATH, you need to make that change yourself.**

Using snaps also works quite well:

```
# This will give you the latest version of go
$ snap install --classic go
```
> A restart is required for the command to be recognized.

If you're using Ubuntu 16.04 LTS and are unable to install `golang-1.10-go`, then you can also use the `longsleep/golang-backports` PPA:

```
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt-get update
sudo apt-get install golang-go
```