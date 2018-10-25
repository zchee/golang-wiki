## Table of Contents

* [Initial paper](#initial-paper)
* [Current state](#current-state)
* [Comment Threads](#comment-threads)
* [Blog posts](#blog-posts)
* [Presentations](#presentations)
* [Videos](#videos)
* [Questions](#questions)
* [Projects Related to vgo](#projects-related-to-vgo)

This document collects thoughts and notes about versioned Go modules from the Gophers [#vgo](https://gophers.slack.com/messages/vgo) channel. Invites to Gophers Slack from [here](https://invite.slack.golangbridge.org/).

### Initial paper

The **initial paper** can be read here [https://research.swtch.com/vgo](https://research.swtch.com/vgo).

The **proposal** can be found here [https://github.com/golang/go/issues/24301](https://github.com/golang/go/issues/24301).

The **reference implementation**: [https://go.googlesource.com/vgo/](https://go.googlesource.com/vgo/) and mirrored on Github here: [https://github.com/golang/vgo](https://github.com/golang/vgo).

The **[Go issue tracker](https://golang.org/issues)** is used to track bugs/feature requests. Issues should have the label `modules` and titles starting with `cmd/go` so that they can be automatically categorized. You can read the [existing issues here](https://golang.org/issues?q=is%3Aopen+is%3Aissue+label:modules).

**Note**: The reference implementation was named `vgo`, but support for modules is being integrated into the `go` command itself. The feature within the `go` command is called “versioned Go modules” (or “[[modules]]” for short), not “vgo”.

***

### Current state

Currently, module support is in active development in the main `go` repository, with changes mirrored back to the `vgo` repository. Module support still has some rough edges. You are encouraged to [[try it|Modules]] and give your feedback, share your experience with it, and contribute to it.

For any production workloads, use [dep](https://github.com/golang/dep), or migrate to it if you have not done so already.

The proposal has been accepted and vgo was merged into the Go tree in version 1.11.

You will be able to experiment with the module workflow from Go 1.11 as it is included as an experiment in this release.

***

### Comment Threads

These are threads that have been created from the initial reference manifest:

- **golang-nuts ML:** [Go += Package Versioning](https://groups.google.com/forum/#!topic/golang-nuts/jFPz5yZCPcQ)

- **golang-dev ML:** [Go += Package Versioning](https://groups.google.com/d/topic/golang-dev/MNQwgYHMEcY/discussion), [vgo & semantic import versioning](https://groups.google.com/d/topic/golang-dev/Plc42fslQEk/discussion), [vgo and vendoring](https://groups.google.com/forum/#!topic/golang-dev/FTMScX1fsYk)
- **HackerNews posts:** https://news.ycombinator.com/from?site=swtch.com
- **Reddit:** https://www.reddit.com/domain/research.swtch.com/

- **vgo & vendoring:** https://groups.google.com/forum/#!topic/golang-dev/FTMScX1fsYk
- **vgo & semantic import versioning** https://groups.google.com/forum/#!topic/golang-dev/Plc42fslQEk

***

### Blog posts

- [A Proposal for Package Versioning in Go](https://blog.golang.org/versioning-proposal)
- [Exploring vgo](https://www.calhoun.io/exploring-vgo/)
- [Semantic Import Versioning in the wild](http://blog.ezyang.com/2018/02/semantic-import-versioning-in-the-wild/)
- [Diving into vgo from the Golang project](https://www.wolfe.id.au/2018/03/01/diving-into-vgo-from-the-golang-project/)
- [Notes on migrating to a Go mono repo](https://github.com/myitcv/x/wiki/Notes-on-migrating-to-a-Go-mono-repo)

***

### Presentations

- [Repeatable Builds with vgo](https://talks.bjk.fyi/gcru18-vgo.html#/)

***

### Videos

- [Opening keynote: Go with Versions - GopherConSG 2018](https://www.youtube.com/watch?v=F8nrpe0XWRg)
- [1-Using vgo for Go Dependency Management](https://www.gophersnacks.com/programs/using-vgo-for-go-dependency-management) by Brian Ketelsen
- [2-Adding External Dependencies with vgo](https://www.gophersnacks.com/programs/adding-external-dependencies-with-vgo)
- [Building Predictability into Your Pipeline](https://www.youtube.com/watch?v=sbrZfPgNmfw) with Russ Cox, Jess Frazelle, Sam Boyer, Pete Garcin.

***

### Projects Related to module support

- [Athens](https://github.com/gomods/athens) - A proxy server for Go modules
- [vgo-docker-example](https://github.com/elithrar/vgo-docker-example) - An example of how to use modules + Docker together.
- [`myitcv.io/cmd/modpub`](https://github.com/myitcv/x/tree/master/cmd/modpub) - a tool to help create a directory of modules from a git repository
- [JFrog Artifactory](https://jfrog.com/artifactory) - A universal artifact repository with module support.

***

### Questions

| Question | Answer |
| ------------- | ------------- |
| Hitting GitHub API rate limits? | Create a token and add it to .netrc, see [related issue](https://golang.org/issues/23955) |
| How does vgo handles dependencies of older, discarded versions [link](https://gophers.slack.com/archives/C9BMAAFFB/p1519493604000033)? | [https://github.com/zeebo/vgo-test-version-selection](https://github.com/zeebo/vgo-test-version-selection) |
| Why are major versions in import paths? | https://groups.google.com/forum/#!topic/golang-dev/Plc42fslQEk |
| How to `go get` so that I can run a program, not download a library? | https://gophers.slack.com/archives/C9BMAAFFB/p1519687366000101 |
| What's the best way to maintain a package repository that have the major version in the import path? | https://groups.google.com/d/topic/golang-nuts/nS6ST60dwF8/discussion, https://groups.google.com/d/topic/golang-nuts/VREgKrQRFcY/discussion |