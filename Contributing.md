---
title: Contributing
---

The contents of https://go.dev/wiki are hosted in the [go.googlesource.com/wiki](https://go.googlesource.com/wiki) repository,
and is also mirrored on https://github.com/golang/wiki.

These contents are served by the same server that hosts the official Go website https://go.dev/.
The server's source is located in the [go.googlesource.com/website](https://go.googlesource.com/website) repository.

## Reporting issues

For issues related to existing contents, the preferred method of resolution is to send a [change](#updating-contents).

However, if you would like to add a new page, please first open an issue in the [Go issue tracker](https://go.dev/issues/new?title=wiki:) with the prefix `wiki:` to propose the addition. Clearly state why the content does not fit into any of the existing pages.

Because renaming of pages in the wiki can break external links, please open an issue before renaming or removing any wiki page.

If the issue pertains to the serving of contents, please open a [GitHub issue](https://go.dev/issues/new?title=x/website:).

### Triaging issues

To address content-related issues, it is recommended to identify the person or team most familiar with the content in question.
A good starting point is the [project owners](https://dev.golang.org/owners) page.

For issues related to content serving, follow the usual triaging process similar to x/website issues
and label them with `website`.

## Updating contents

Before making changes, ensure familiarity with the code review process outlined in
the official [Contribution Guide](/doc/contribute).

### Sending a trivial change

For minor updates such as fixing typos and adding missing links, you can use
the [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow).
Make edits from the [GitHub repo](https://github.com/golang/wiki) and open a GitHub pull request as you normally would.

Additional information is available at [Sending a change via GitHub](/doc/contribute#sending_a_change_github).

### Sending a non-trivial change

For larger changes, consider sending your change through Gerrit following the instructions provided in
[Sending a change via Gerrit](/doc/contribute#sending_a_change_gerrit).

The canonical repository for wiki content is located at `go.googlesource.com/wiki`.

```
$ git clone https://go.googlesource.com/wiki
```
<!-- TODO: describe supported markdown syntaxes, and how to test local changes -->

## Reviewing and submitting changes

Unlike other Go repositories, the submission process for the wiki repository
requires only one +2 from anyone in the wiki repository maintainers group.
See [Proposal 61940](https://go.dev/issues/61940) for additional background.

**Note for reviewers**: once you give your +2 and all comments are addressed,
please merge the change soon to avoid merge conflicts.

Anyone interested in receiving notifications about incoming wiki CLs
can opt-in through their [Gerrit notifications](https://go-review.googlesource.com/settings/#Notifications).

## Changing and testing the contents serving behavior

[`golang.org/x/website/cmd/golangorg`](https://golang.org/x/website/cmd/golangorg)
is the program that serves the wiki pages.

```
$ git clone https://go.googlesource.com/website
$ cd website/cmd/golangorg
```

Follow the [instructions in README.md](https://cs.opensource.google/go/x/website/+/master:cmd/golangorg/README.md) for running and testing the program locally.