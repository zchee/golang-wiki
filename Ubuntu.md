## Install package ` golang `

The ` golang ` Debian package may have already made its way into your Ubuntu distribution. Try this:

```
   sudo apt-get install golang
```

## If that didn't work

If you have an arm, i386, or amd64, with the Ubuntu Lucid, Maverick,
Natty, Oneiric, or Precise release, you can easily install Go 1 right
now as a package by running:

(link to ppa is broken)

```
   sudo add-apt-repository ppa:gophers/go
   sudo apt-get update
   sudo apt-get install golang-stable
```

(If you don't have ` add-apt-repository `, run "` sudo apt-get install python-software-properties `".)

The ` golang-stable ` package includes everything necessary for developing
with Go. There are also ` golang-tip ` and ` golang-weekly ` packages in the
same repository, and these are up-to-date, except ` golang-weekly ` isn't
really interesting at the moment since golang-stable is more recent.