The GOPATH environment variable specifies the location of your workspace. By default it is `$HOME/go` on Unix systems and `%USERPROFILE%\go` on Windows. If you want to use a custom location as your workspace, you can set the GOPATH env variable. This page explains how to set this variable on various platforms.


- [Unix systems](#unix-systems)
  * [Bash](#bash)
  * [Zsh](#zsh)
- [Windows](#windows)

# Unix systems

`GOPATH` can be any directory on your system. In Unix examples, we will set it to `$HOME/work`. Note that `GOPATH` must not be the same path as your Go installation. Another common setup is to set GOPATH=$HOME.

## Bash

Edit your `.bash_profile` to add the following line:
```bash
export GOPATH=$HOME/work
```

Save and exit your editor. Then, source your `~/.bash_profile`.
```bash
$ source ~/.bash_profile
```

> Note: Set the GOBIN path to generate a binary file when run "go install"
> ```bash
> export GOBIN=$HOME/work/bin
> ```

## Zsh

Edit `~/.zshrc` file to add the following line:

```bash
export GOPATH=$HOME/work
```
Save and exit your editor. Then, source your `~/.zshrc`.
```bash
$ source ~/.zshrc
```

# Windows

Your workspace can be located wherever you like,
but we'll use `C:\work` in this example.
Note that `GOPATH` must not be the same path as your Go installation.

* Create folder at `C:\work`.
* Right click on "Start" and click on "Control Panel". Select "System and Security", then click on "System".
* From the menu on the left, select the "Advanced systems settings".
* Click the "Environment Variables button at the bottom.
* Click "New" from the "User variables" section.
* Type `GOPATH` into the "Variable name" field.
* Type `C:\work` into the "Variable value" field.
* Click OK.
