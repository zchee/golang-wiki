## Table of Contents

* [Initial paper](#initial-paper)
* [Current state](#current-state)
* [Comment Threads](#comment-threads)
* [Blog posts](#blog-posts)
* [Videos](#videos)
* [Questions](#questions)

This document collects thoughts and notes about vgo from the Gophers [#vgo](https://gophers.slack.com/messages/vgo) channel. Invites to Gophers Slack from [here](https://invite.slack.golangbridge.org/).

### Initial paper

The **initial paper** can be read here [https://research.swtch.com/vgo](https://research.swtch.com/vgo).

The **reference implementation**: [https://go.googlesource.com/vgo/](https://go.googlesource.com/vgo/) and mirrored on Github here: [https://github.com/golang/vgo](https://github.com/golang/vgo).

The **[Go issue tracker](https://golang.org/issues)** will be used to track bugs / feature requests for vgo. The issues will need to start with ` x/vgo ` so that they can be automatically categorized. You can read the [existing issues here](https://golang.org/issues?q=is%3Aopen+is%3Aissue+milestone%3Avgo).

### Current state

Currently vgo is in active development / prototype phase. It has some rough edges, changes will happen at a rapid pace. You are encouraged to try vgo and give your feedback, share your experience with it, and contribute to it.

For any production workloads, use [dep](https://github.com/golang/dep), or migrate to it if you have not done so already.

vgo will be merged in the Go tree and replace dep at a later date.

### Comment Threads

These are threads that have been created from the initial reference manifest for vgo:

- **golang-nuts ML:** [https://groups.google.com/forum/#!topic/golang-nuts/jFPz5yZCPcQ](https://groups.google.com/forum/#!topic/golang-nuts/jFPz5yZCPcQ)
- **golang-dev ML:** [https://groups.google.com/forum/#!topic/golang-dev/MNQwgYHMEcY](https://groups.google.com/forum/#!topic/golang-dev/MNQwgYHMEcY)
- **HackerNews posts:** https://news.ycombinator.com/from?site=swtch.com
- **Reddit:** https://www.reddit.com/domain/research.swtch.com/

***

### Blog posts

- [Thoughts on vgo and dep](https://sdboyer.io/blog/vgo-and-dep/)
- [Exploring vgo](https://www.calhoun.io/exploring-vgo/)
- [Semantic Import Versioning in the wild](http://blog.ezyang.com/2018/02/semantic-import-versioning-in-the-wild/) (blogpost)

***

### Videos

[Building Predictability into Your Pipeline](https://www.youtube.com/watch?v=sbrZfPgNmfw) With Russ Cox, Jess Frazelle, Sam Boyer, Pete Garcin.

***

### Questions

| Question | Answer |
| ------------- | ------------- |
| Hitting GitHub API rate limits? | Create a token and add it to .netrc, see [related issue](https://golang.org/issues/23955) |
| How does vgo handles dependencies of older, discarded versions [link](https://gophers.slack.com/archives/C9BMAAFFB/p1519493604000033) | [https://github.com/zeebo/vgo-test-version-selection](https://github.com/zeebo/vgo-test-version-selection) |
