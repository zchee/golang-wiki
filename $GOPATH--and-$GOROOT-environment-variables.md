$GOPATH  and $GOROOT environment variables very important in golang world.

$GOROOT is the directory what you installed golang.

If you installed golang by download binary package.

It could be $HOME/go

we can set it up by add one line in $HOME/.bashrc

```bash
export GOROOT=$HOME/go
```

$GOPATH is your golang workspace, your third party libraries will install in $GOPATH

If you have not set GOPATH, you should create one empty directory first.

For example, create $HOME/goworkspace

and add one line in $HOME/.bashrc

```bash
export GOPATH=$HOME/goworkspace
```
And we should put the bin directory in $PATH variable

Add one line to $HOME/.bashrc

```bash
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
```
