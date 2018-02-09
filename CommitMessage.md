# Commit messages

Commit messages for Go repos should be formatted as follows:

```
net/http: frob the quux before blarfing

Fixes #nnnn
```

Notably,

* the package name goes before the colon
* the part after the colon uses the verb tense + phrase that completes the blank in, *"This change modifies Go to ___________"*
* lowercase verb after the colon
* no trailing period

If it's not a complete fix and more is coming, use:

```
Updates #nnn
```

... instead of `Fixes`. Don't use the other GitHub-supported verbs.

# Other repos

For non-"go" repos ("crypto", "tools", "net", etc), the subject is still the name of the package, but you need to fully-qualify the issue number with the GitHub org/repo syntax:

```
cipher/rot13: add new super secure cipher

Fixes golang/go#1234
````
