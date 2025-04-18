---
title: Gomote
---

The gomote command is a client for the Go builder infrastructure. It's a remote control for remote Go builder machines.

## Installation

```
$ go install golang.org/x/build/cmd/gomote@latest  # Go 1.16 and later
```

## Usage

The most basic usage of the gomote tool involves just a few steps:
1. Create an instance.
1. Push code to the instance.
1. Run commands on the instance.

Running the `create` command with the `-list` flag will list available instance types.

```
$ gomote create -list
(list tons of builder types)
```

Then, an instance can be created by specifying an instance type. The instance's name will be printed to stdout, so the result may be stored in an environment variable. (There may be other logging messages, but they will be on stderr and each line will have a '#' prefix.)

```
$ gomote create gotip-linux-amd64
# still creating gotip-linux-amd64 (1) after 5s; 0 requests ahead of you
user-gotip-linux-amd64-0
```

With that instance's name you can now push a GOROOT to the instance and install a bootstrap toolchain. The repository you sync will appear at the `go` subdirectory of `$WORKDIR` (the default directory of all gomote operations). The bootstrap toolchain will always go into the `go1.4` subdirectory (even if the bootstrap toolchain isn't from version 1.4).

```
$ GOROOT=/path/to/local/go/repo gomote push user-gotip-linux-amd64-0
$ gomote ls user-gotip-linux-amd64-0
go
go1.4
```

Note that `push` really is a "sync" operation, so next time you push the gomote tool will only push what has changed (files added, modified, or removed).

With a toolchain installed, you can now build it by running commands on the instance. The `run` command allows you to specify an executable to run. The executable must be specified relative to `$WORKDIR` (e.g. `go/bin/go`) or via an absolute path (e.g. `/bin/bash`). That executable will then run with its current working directory set to the directory containing the executable.

```
$ gomote run user-gotip-linux-amd64-0 go/src/make.bash
```

To then run the built Go toolchain, use `go/bin/go`.

```
$ gomote run user-gotip-linux-amd64-0 go/bin/go test -run="TestSomething" -v runtime
```

You can additionally specify a working directory and environment variables via flags to `run` that will be applied before the command is executed.

Note that gomote instances will automatically disappear after 30 minutes of inactivity. Use the `list` command to check how long they have left.

```
$ gomote list
user-gotip-linux-amd64-0	gotip-linux-amd64	gotip-linux-amd64	expires in 10m27.339494527s
```

The `ping` command can be used to keep an instance alive if no other commands are being run against it.

For more information on each command run `gomote help <command>`. For more commands, run `gomote help`.

### Builder types

Available builder types follow a certain structure, loosely `$GOBRANCH-($REPO-)?$GOOS-$GOARCH(_$OS)-$EXTRA`.

A few useful notes about these names.
- Different `$GOBRANCH` mainly modify the preinstalled tool versions, like the bootstrap Go toolchain.
- Builder types with `$REPO` will have the specified repository downloaded to the work root at tip-of-tree.

### Debugging buildlets directly

The `create` command contacts the build coordinator (farmer.golang.org) and requests that it create the buildlet on your behalf. All subsequent commands (such as `gomote run` or `gomote ls`) then proxy your request via the coordinator.  To access a buildlet directly (for example, when working on the buildlet code), you can skip the `gomote create` step and use the special builder name `<build-config-name>@ip[:port>`, such as `windows-amd64-2008@10.1.5.3`.

### Groups

Instances may be managed in named groups, and commands are broadcast to all instances in the group.

A group is specified either by the `-group` global flag or through the `GOMOTE_GROUP` environment variable. The `-group` flag must always specify a valid group, whereas `GOMOTE_GROUP` may contain an invalid group. Instances may be part of more than one group.

Groups may be explicitly managed with the "group" subcommand, but there are several short-cuts that make this unnecessary in most cases:

- The `create` command can create a new group for instances with the `-new-group` flag.
- The `create` command will automatically create the group in `GOMOTE_GROUP` if it does not exist and no other group is explicitly specified.
- The `destroy` command can destroy a group in addition to its instances with the `-destroy-group` flag.

As a result, the easiest way to use groups is to just set the `GOMOTE_GROUP` environment variable:

```
$ export GOMOTE_GROUP=debug
$ gomote create gotip-linux-amd64
$ GOROOT=/path/to/goroot gomote push
$ gomote run go/src/make.bash
```

As this example demonstrates, groups are useful even if the group contains only a single instance: it can dramatically shorten most gomote commands.

## Tips and tricks

### General

The `create` command accepts the `-setup` flag which also pushes a `GOROOT` and runs the appropriate equivalent of `make.bash` for the instance.

Example:
```
$ GOROOT=/path/to/my/goroot gomote create -setup gotip-linux-amd64
# Creating user-gotip-linux-amd64-0...
# Pushing /path/to/my/goroot to user-gotip-linux-amd64-0
# Running make.bash on user-gotip-linux-amd64-0...
```

The `create` command accepts the `-count` flag for creating several instances at once.

Example:
```
$ gomote create -count=3 gotip-linux-amd64
# Creating user-gotip-linux-amd64-0...
# Creating user-gotip-linux-amd64-1...
# Creating user-gotip-linux-amd64-2...
```

The `run` command accepts the `-collect` flag for automatically writing the output from the command to a file in the current working directory, as well as a copy of the full file tree from the instance. This command is useful for capturing the output of long-running commands in a set-and-forget manner.

Example:
```
$ gomote run -collect user-gotip-linux-amd64-0 /bin/bash -c 'echo hi'
# Writing output to user-gotip-linux-amd64-0.stdout...
$ cat user-gotip-linux-amd64-0.stdout
hi
$ ls user-gotip-linux-amd64-0.tar.gz
user-gotip-linux-amd64-0.tar.gz
```

The `run` command accepts the `-until` flag for continuously executing a command until the output of the command matches some pattern. This is useful for reproducing rare issues, and especially useful when used together with `-collect`.

Example:
```
$ gomote run -until 'FAIL' -collect user-gotip-linux-amd64-0 go/bin/go test -run 'TestFlaky' -count=1000 runtime
# Writing output to user-gotip-linux-amd64-0.stdout...
$ cat user-gotip-linux-amd64-0.stdout
...
--- FAIL: TestFlaky ---
...
$ ls user-gotip-linux-amd64-0.tar.gz
user-gotip-linux-amd64-0.tar.gz
```

Note that the `run` command always streams output to a temporary file regardless of any additional flags to avoid losing output due to terminal scrollback. It always prints the location of the file.

#### Reproducing a rare failure

Putting together some of the tricks above and making use of groups, it's much easier to hammer on some test to try to reproduce a rare failure. For example:

```
$ export GOMOTE_GROUP=debug
$ GOROOT=/path/to/goroot gomote create -setup -count=10 gotip-linux-amd64
$ gomote run -until='unexpected return pc' -collect go/bin/go run -run="TestFlaky" -count=100 runtime
```

### Darwin

Darwin gomotes are known to take a few minutes to set up, even if there are machines available.
This is due to the extra time necessary to set up Xcode.

### Windows

```
$ gomote run -path '$PATH,$WORKDIR/go/bin' $MOTE go/src/make.bat
$ gomote run -path '$PATH,$WORKDIR/go/bin' $MOTE go/bin/go.exe test cmd/go -short
```

Note: previous versions of the wiki have advised setting GOROOT for gomote 'run' commands (e.g. "-e GOROOT=%WORKDIR%\go"); this is no longer recommended (causes problems with Go command caching).

### Subrepos on Windows

```
$ tar --exclude .git -C ~/go/src/ -zc golang.org/x/tools | gomote puttar -dir=gopath/src $MOTE -
$ gomote run -e 'GOPATH=%WORKDIR%\gopath' $MOTE go/bin/go test -run=TestFixImportsVendorPackage golang.org/x/tools/imports
```

If ssh'd into the machine, these envvars may be handy:

```
$ set GOPATH=%WORKDIR%\gopath
$ set PATH=%PATH%;%WORKDIR%\gopath\bin;%WORKDIR%\go\bin
$ set CGO_ENABLED=0
```

### Subrepos on Unix

Testing golang.org/x/sys/unix on $MOTE

```
$ tar -C $GOPATH/src/ -zc golang.org/x/sys/unix | gomote puttar -dir=gopath/src $MOTE
$ gomote run -e 'GOPATH=/tmp/workdir/gopath' -dir 'gopath/src/golang.org/x/sys/unix' $MOTE go/bin/go test -v golang.org/x/sys/unix
```

(The GOPATH part is for GOPATH compatibility mode; the `-dir` is for modules mode, which looks in the working directory and up for `go.mod`)

### Android

```
export MOTE=`gomote create android-arm64-wikofever`
gomote push $MOTE
gomote run $MOTE go/src/make.bash
```
PATH must contain the exec wrapper, `go_android_*_exec`, built by make.bash.

```
gomote run -path '$PATH,$WORKDIR/go/bin' $MOTE go/bin/go test math/big
```

## About buildlets

https://farmer.golang.org/builders lists information about how each buildlet is deployed and configured.
The information is from golang.org/x/build/dashboard and golang.org/x/build/env.

## Access

**Effective January 2025, gomote access will automatically be granted to contributors who have [Approvers](https://go.dev/wiki/GerritAccess#approving-cls-approvers) access.**

**On August 2022, a new infrastructure was deployed which required the removal of all gomote access from previously approved users. Please re-request access if you still require access.**

To request access to the gomote service, file a new issue (https://go.dev/issue/new?title=access:+&body=See+https://go.dev/wiki/Gomote%23access.) and state the Google account you use to log in to Gerrit. The provided account will only be used for authentication purposes.

Authentication is triggered with the first invocation of a command:

```
$ gomote create gotip-linux-amd64
Please visit https://www.google.com/device in your browser and enter verification code:
 ABCD-4567
...
```

The login command will also initiate the authentication workflow:

```
$ gomote login
Please visit https://www.google.com/device in your browser and enter verification code:
 ABCD-4567
...
```

After opening a browser with the provided link the user must authenticate with the google account and paste the verification code into the browser. After a short wait the client will be authenticated.

### gomote ssh

The `gomote ssh` command uses a SSH keys created specifically for gomote. On the first use of the `gomote ssh` a set of keys will be created and stored in the local user configuration directory. You may be asked to add set a password for the keys (a password is not required). The SSH functionality operates with OpenSSH certificate authentication and does not require any additional configuration. Not all builder types support `gomote ssh`.
