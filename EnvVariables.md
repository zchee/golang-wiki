# Environment Variables

This page contains guides to set Go environment variables on various operating systems.

## Setting GOPATH

### Unix systems

`GOPATH` can be any directory on your system. In Unix examples, we will set it to `$HOME/work`. Note that `GOPATH` must not be the same path as your Go installation. Another common setup is to set GOPATH=$HOME.

#### Bash

Edit your `.bash_profile` to add the following line:
```bash
export GOPATH=$HOME/work
```

Save and exit your editor. Then, source your `~/.bash_profile`.
```bash
$ source ~/.bash_profile
```

#### Zsh

Edit `~/.zshrc` file to add the following line:

```bash
export GOPATH=$HOME/work
```
Save and exit your editor. Then, source your `~/.zshrc`.
```bash
$ source ~/.zshrc
```

### Windows

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


