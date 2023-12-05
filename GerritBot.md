---
title: GerritBot
---

GerritBot is a tool used for importing GitHub Pull Requests (PRs) into [Gerrit](https://go-review.googlesource.com) for code review. It was created because the Go team does all its reviews in Gerrit, but we'd like to allow a more common workflow for contributing code via GitHub PRs.

Table of Contents
=================

+ [Workflow](#workflow)
+ [Frequently Asked Questions](#frequently-asked-questions)
+ [Feedback and Bug Reports](#feedback-and-bug-reports)
+ [I'd like to add a feature/fix a bug](#id-like-to-add-a-featurefix-a-bug)

## Workflow

+ A user can upload a GitHub PR against any of our GitHub repos just as they would with any other GitHub project that accepts PRs
+ The PR changes will then be imported by GerritBot and a message will be posted to the GitHub PR containing a link to the Gerrit review
+ All comments are handled within Gerrit. Any comments on the GitHub PR will be ignored
+ The PR author can continue to upload commits to the branch used by the PR in order to address feedback from Gerrit
+ Any changes to the commit message must be done by editing the title and description of the GitHub PR, and not via Gerrit or git. (See FAQ below for details).
+ [Draft PRs](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests) are imported as [WIP](https://gerrit-review.googlesource.com/Documentation/intro-user.html)
+ Once the code is ready to be merged, a maintainer will submit the change on Gerrit and GerritBot will close the issue
+ Similarly, if a change is closed or abandoned on Gerrit, the corresponding PR will be closed

## Frequently Asked Questions

### I need a Google account to sign up for Gerrit? Why can't I sign in using my GitHub account?

You need a Gmail or other Google account to [register for Gerrit](https://go-review.googlesource.com/login/).
This is a limitation of the infrastructure that runs our Gerrit instances and is out of our control, plus you already need a Google account to [sign our CLA](https://cla.developers.google.com/clas), a requirement for us to accept your contribution in the first place.

### I left a reply to a comment in Gerrit but no one but me can see it

Replies to comments on code in Gerrit are first saved as drafts and need to be published via the “Reply” button. This is to prevent multiple emails per review “session” and is similar to the [pending review workflow](https://help.github.com/articles/reviewing-proposed-changes-in-a-pull-request/) in GitHub. If you see a number next to the “Reply” text in the button, this means you have pending drafts to publish.

### How does GerritBot determine the final commit message?

It uses the title and description of the GitHub PR to construct the commit message for the Gerrit change. You can edit this using the GitHub web interface (not Gerrit or git). The PR description is in the first text area in the "Conversation" tab of the GitHub PR. It is editable via "Edit" option on the "..." menu. 

**Note:** Gerrit imports the **plain** text that is viewable as you edit the message in Github, and it does not import the **rendered** text you see in GitHub prior to editing.

One common area of related confusion is around **issue references**. For example, GerritBot or a human reviewer might ask you to [avoid URLs for issue references](https://go.dev/doc/contribute#ref_issues). In Gerrit, you might see the full URL for an issue, but in the GitHub web interface, you might only see an issue reference like `#12345` and it might be unclear where the URL is coming from. This can be due to confusion between the rendered view in GitHub vs. the underlying raw/plain text. If the GitHub web interface shows something like `Fixes https://github.com/golang/go/issues/12345` while you are **editing the text in GitHub**, change it to something like `Fixes #12345` or `Fixes golang/go#12345` instead. See the [Contribution Guide](https://go.dev/doc/contribute#ref_issues) for more on issue references.

Once the PR is edited in GitHub, it can take 10 minutes or so before the Gerrit change is updated.

### What is a CL? What is a Gerrit change?

CL is short for "change list", which is essentially a patch proposed to be introduced into a repository. The Go project uses Gerrit to carefully review each CL. An example CL is https://go.dev/cl/508475.

Gerrit change is another term for CL.

### Can I help review other people's CLs?

Yes, this is highly encouraged, and a great way to familiarize yourself with Gerrit, the Go project's [code review process](https://go.dev/doc/contribute#review), and the internals of the Go standard library, runtime, compiler, and so on.

You can browse the currently open CLs [here](https://go-review.googlesource.com/q/status:open+-is:wip) and subscribe for updates to interesting CLs by clicking the star icon.

You don't need to be an expert in the code to help with initial review triage. See the section on [helping to review CLs](/wiki/Gardening/#pending-cls) in the [Gardening](/wiki/Gardening) wiki page for more details.

### I heard Gerrit requires one commit per change. Can I upload multiple commits to my PR?

You can upload as many commits as you like. GerritBot will handle squashing your commits into one change that Gerrit can handle.

### Why is GerritBot the owner of my change?

This is due to an [open bug](https://bugs.chromium.org/p/gerrit/issues/detail?id=8296) with the way Gerrit handles acting as another user. Once that is fixed, the original author will also be the owner of the change.

### Can I ask GerritBot to stop posting comments on my PR?

You can toggle comments from GerritBot by using the `comments` slash command (e.g., `/comments off`).

## Feedback and Bug Reports

Please [file an issue](https://github.com/golang/go/issues/new?title=x%2Fbuild%2Fcmd%2Fgerritbot%3A%20%3Cfill%20this%20in%3E) and use the `x/build/cmd/gerritbot:` prefix in the title.

## I'd like to add a feature/fix a bug

+ If the feature/bug is non-trivial, please [file an issue](https://github.com/golang/go/issues/new?title=x%2Fbuild%2Fcmd%2Fgerritbot%3A%20%3Cfill%20this%20in%3E) first
+ The code is located at x/build/cmd/gerritbot
  ([GitHub](https://github.com/golang/build/tree/master/cmd/gerritbot),
  [Gerrit](https://go.googlesource.com/build/+/master/cmd/gerritbot/))
