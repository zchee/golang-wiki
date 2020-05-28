### Be sure to familiarize yourself with the code review process from the official [Contribution Guide](https://golang.org/doc/contribute.html) first.

# Reviewer Parlance

There are several terms code reviews may use that you should become familiar with.

* ` LGTM ` — looks good to me
* ` SGTM ` — sounds good to me
* ` PTAL ` — please take a look
* ` s/foo/bar/ ` — please replace ` foo ` with ` bar `; this is [sed syntax](http://en.wikipedia.org/wiki/Sed#Usage)
* ` s/foo/bar/g ` — please replace ` foo ` with ` bar ` throughout your entire change

# CL Directives

* `R=foo` — assign a reviewer within the [Go CL dashboard](https://swtch.com/godash/)
* `RELNOTE=yes` or `RELNOTE=<subject>` — tag for release notes; scraped by the [relnote](https://golang.org/x/build/cmd/relnote) tool
*  (in the commit message) — block submission; see the "Work in progress"
* `Updates #1234` on(in the commit message) — link the C from the GitHub issue and optionally close the issue after the C is merged

# Email

Messages from a code review are typically sent to three places:

* the reviewers, 
* the golang-code group
* the review


# Work in progress

If you have changes that aren't ready to be reviewed, you can put a giant **`DO NOT REVIEW`** as the second line of the CL description, so that people who see it know not to look any further. Don't make it the first line, since then it will become the subject for the entire review, even after you've changed the description.

Similarly, if you would like to ensure that your changes are not merged by mistake, you can put second line of the C description.

If you  need Gerrit's features, but just want to backup your work, share work between multiple clients, or have a staging UI to examine your changes, you can use a regular git .

To use GitHub as a git remote, you can either fork github.com/golang/go or create . There are trade-offs. Forked repos will have a faster first push. forked repos can be private. Forked repos are associated in GitHub's system. As a result, they are easily discoverable and support cross-repo comparisons in the GitHub UI; however, that references to issues in commit messages in forked repos will create references to your fork in the issue.

To add your git remote, run something like:

```bash
$ git remote 
```

You can then push changes to the "fork" remote with `git push fork `.

Gerrit's code review model is to rewrite a single commit until it is correct. GitHub will try to prevent you from accidentally overwriting your existing branch. You can work around this by forcing the push: `git push --force fork branchname`. Alternatively, you can set up your forked remote as a mirror by cloning it initially with:

```bash
$ git remote add --mirror=push fork 
```

Then running `git push fork` will update GitHub to  (all branches, all tags, etc.). This is handy, but take care when using this on multiple clients. You are bypassing the usual git safeguards, so it is easy to overwrite (and thus lose) work pushed by a different client.