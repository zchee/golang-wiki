## Table of Contents

* [Initial paper](#initial-paper)
* [Current state](#current-state)
* [Comment Threads](#comment-threads)
* [Blog posts](#blog-posts)
* [Presentations](#presentations)
* [Videos](#videos)
* [Questions](#questions)
* [Projects Related to vgo](#projects-related-to-vgo)

This document collects thoughts and notes about vgo from the Gophers [#vgo](https://gophers.slack.com/messages/vgo) channel. Invites to Gophers Slack from [here](https://invite.slack.golangbridge.org/).

### Initial paper

The **initial paper** can be read here [https://research.swtch.com/vgo](https://research.swtch.com/vgo).

The **proposal** can be found here [https://github.com/golang/go/issues/24301](https://github.com/golang/go/issues/24301).

The **reference implementation**: [https://go.googlesource.com/vgo/](https://go.googlesource.com/vgo/) and mirrored on Github here: [https://github.com/golang/vgo](https://github.com/golang/vgo).

The **[Go issue tracker](https://golang.org/issues)** is used to track bugs / feature requests for vgo. The issue titles need to start with `x/vgo` so that they can be automatically categorized. You can read the [existing issues here](https://golang.org/issues?q=is%3Aopen+is%3Aissue+milestone%3Avgo).

***

### Current state

Currently vgo is in active development / prototype phase. It has some rough edges, changes will happen at a rapid pace. You are encouraged to try vgo and give your feedback, share your experience with it, and contribute to it.

For any production workloads, use [dep](https://github.com/golang/dep), or migrate to it if you have not done so already.

vgo will be merged in the Go tree and replace dep at a later date, assuming the proposal is accepted.

***

### Comment Threads

These are threads that have been created from the initial reference manifest for vgo:

- **golang-nuts ML:** [Go += Package Versioning](https://groups.google.com/forum/#!topic/golang-nuts/jFPz5yZCPcQ)

- **golang-dev ML:** [Go += Package Versioning](https://groups.google.com/d/topic/golang-dev/MNQwgYHMEcY/discussion), [vgo & semantic import versioning](https://groups.google.com/d/topic/golang-dev/Plc42fslQEk/discussion), [vgo and vendoring](https://groups.google.com/forum/#!topic/golang-dev/FTMScX1fsYk)
- **HackerNews posts:** https://news.ycombinator.com/from?site=swtch.com
- **Reddit:** https://www.reddit.com/domain/research.swtch.com/

- **vgo & vendoring:** https://groups.google.com/forum/#!topic/golang-dev/FTMScX1fsYk
- **vgo & semantic import versioning** https://groups.google.com/forum/#!topic/golang-dev/Plc42fslQEk

***

### Blog posts

- [Thoughts on vgo and dep](https://sdboyer.io/blog/vgo-and-dep/)
- [Exploring vgo](https://www.calhoun.io/exploring-vgo/)
- [Semantic Import Versioning in the wild](http://blog.ezyang.com/2018/02/semantic-import-versioning-in-the-wild/)
- [Diving into vgo from the Golang project](https://www.wolfe.id.au/2018/03/01/diving-into-vgo-from-the-golang-project/)
- [A Proposal for Package Versioning in Go](https://blog.golang.org/versioning-proposal)
***

### Presentations

- [Repeatable Builds with vgo](https://cda.ms/jD)

***

### Videos

- [1-Using vgo for Go Dependency Management](https://www.gophersnacks.com/programs/using-vgo-for-go-dependency-management) by Brian Ketelsen
- [2-Adding External Dependencies with vgo](https://www.gophersnacks.com/programs/adding-external-dependencies-with-vgo)
- [Building Predictability into Your Pipeline](https://www.youtube.com/watch?v=sbrZfPgNmfw) with Russ Cox, Jess Frazelle, Sam Boyer, Pete Garcin.

***

### Projects Related to vgo

- [Athens](https://github.com/gomods/athens) - A proxy server for vgo
- [vgo-docker-example](https://github.com/elithrar/vgo-docker-example) - An example of how to use vgo + Docker together.

***

### Questions

| Question | Answer |
| ------------- | ------------- |
| Hitting GitHub API rate limits? | Create a token and add it to .netrc, see [related issue](https://golang.org/issues/23955) |
| How does vgo handles dependencies of older, discarded versions [link](https://gophers.slack.com/archives/C9BMAAFFB/p1519493604000033)? | [https://github.com/zeebo/vgo-test-version-selection](https://github.com/zeebo/vgo-test-version-selection) |
| Why are major versions in import paths? | https://groups.google.com/forum/#!topic/golang-dev/Plc42fslQEk |
| How to `go get` so that I can run a program, not download a library? | https://gophers.slack.com/archives/C9BMAAFFB/p1519687366000101 |
| What's the best way to maintain a package repository that have the major version in the import path? | https://groups.google.com/d/topic/golang-nuts/nS6ST60dwF8/discussion, https://groups.google.com/d/topic/golang-nuts/VREgKrQRFcY/discussion |