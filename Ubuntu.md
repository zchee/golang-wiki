Try:

```
$ sudo apt-get install golang-go
```

... but if that's too old for you, try:

```
$ sudo add-apt-repository ppa:gophers/archive
$ sudo apt update
$ sudo apt-get install golang-1.8-go
```

> Note that golang-1.8-go puts binaries in /usr/lib/go-1.8/bin. If you want them on your PATH, you need to make the change yourself.

Using snaps also works quite well:

```
# This will give you the latest version of go
$ snap install --classic go
```

Or use Go's official (non-Deb) downloads:

https://golang.org/dl/

If you're using Ubuntu 16.04 LTS and are unable to install `golang-1.8-go`, then you can also use the `longsleep/golang-backports` PPA:

```
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt-get update
sudo apt-get install golang-go
```

