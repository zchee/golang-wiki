# Introduction

Tips for hacking on Go and having multiple ` $GOROOT ` workspaces...

Sometimes you need to check out multiple copies of the Go tree, perhaps you're working on several core library changes at once and you want to test them independently.

Let's say you've checked the trees out as ` $HOME/go1 `, ` $HOME/go2 `, etc.  (The specific names are not important.)  While you're working in each tree, it's important that you always set ` GOROOT ` to the correct tree or unexpected things will happen, like binaries will be built from sources other than the ones you've just edited.  Such mistakes can be time-consuming to notice, and it's easy to forget to update ` GOPATH ` when you change directories.  The following trick may be helpful.

Define a script called ` go `, and ensure its directory is on your ` PATH ` or define a shell alias ` go ` that points to it.  In the script, set the ` GOROOT ` and (if you like) ` GOPATH ` environment variables to appropriate values determined from your current working directory.  Then exec the real ` go ` command.

For example:

```
#!/bin/sh
# Set GOROOT to the innermost enclosing directory containing
# an AUTHORS file.  Set GOPATH to its child called "got".
dir=$(pwd)
while true; do
  if [ -f "$dir/AUTHORS" ]; then
    export "GOROOT=$dir"
    export "GOPATH=$GOROOT/got"
    echo "GOROOT=$GOROOT" >&2
    echo "GOPATH=$GOPATH" >&2
    break
  fi
  dir=$(dirname "$dir")
  if [ "$dir" = / ]; then
    echo "Can't locate GOROOT". >&2
    exit 1
  fi
done
exec "$GOROOT/bin/go" "$@"
```