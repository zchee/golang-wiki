# Commit messages

Commit messages, also known as CL (changelist) descriptions, for Go repos should be formatted as follows:

```
net/http: frob the quux before blarfing

Fixes #nnnn
```

Notably,

* the package name goes before the colon
* the part after the colon uses the verb tense + phrase that completes the blank in, *"This change modifies Go to ___________"*
* lowercase verb after the colon
* no trailing period
* keep the subject (first line) as short as possible. ideally under 76 characters or shorter.
* keep the body wrapped too, also max 76, unless it's really needed (ASCII art, table, or long link)
* the Fixes/Updates line should be after the body with a blank newline separating the two
* no Markdown
* we **do not** use `Signed-off-by` lines in Go. Please don't add them. Our Gerrit server & GitHub bots enforce CLA compliance instead.

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

Notably, the first line subject should **not** contain the `x/crypto/` prefix. We only do that for the issue tracker.

# Non-normative references

- [Please heed my plea and write good CL descriptions for Go—and for any other project you work on.](https://groups.google.com/d/msg/golang-dev/6M4dmZWpFaI/SyU5Sl4zZLYJ)
- [The CL description is a public document that explains to the future what has been done and why.](https://groups.google.com/d/msg/golang-dev/s07ZUR8ZDHo/i-rIsknbAwAJ)

# GitHub Pull Requests

If you're using GitHub Pull Requests, your commit message is constructed by GerritBot based on your
PR's title & description. See https://github.com/golang/go/wiki/GerritBot#how-does-gerritbot-determine-the-final-commit-message

If somebody asks you to modify your commit message, you'll need to modify your PR.