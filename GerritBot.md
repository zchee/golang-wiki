GerritBot is a tool used for importing GitHub Pull Requests (PRs) into [Gerrit](https://go-review.googlesource.com) for code review. It was created because the Go team does all its reviews in Gerrit, but we'd like to allow a more common workflow for contributing code via GitHub PRs.

Table of Contents
=================

+ [Workflow](#workflow)
+ [Feedback and Bug Reports](#feedback-and-bug-reports)
+ [Frequently Asked Questions](#frequently-asked-questions)
+ [I'd like to add a feature/fix a bug](#id-like-to-add-a-featurefix-a-bug)

## Workflow

+ A user can upload a PR against any of our GitHub repos just as they would with any other GitHub project that accepts PRs
+ The PR changes will then be imported by GerritBot and a message will be posted to the GitHub PR Issue containing a link to the Gerrit review
+ All comments are handled within Gerrit. Any comments on the GitHub PR will be ignored
+ The PR author can continue to upload commits to the branch used by the PR in order to address feedback from Gerrit
+ Once the code is ready to be merged, a maintainer will submit the change on Gerrit and GerritBot will close the issue
+ Similarly, if a change is closed or abandoned on Gerrit, the corresponding PR will be closed

## Feedback and Bug Reports

Please [file an issue](https://github.com/golang/go/issues/new?title=x%2Fbuild%2Fcmd%2Fgerritbot%3A%20%3Cfill%20this%20in%3E) and use the `x/build/cmd/gerritbot:` prefix in the title.

## Frequently Asked Questions

### Why is GerritBot the owner of my change?

This is due to an [open bug](https://bugs.chromium.org/p/gerrit/issues/detail?id=8296) with the way Gerrit handles acting as another user. Once that is fixed, the original author will also be the owner of the change.
 
### I heard Gerrit requires one commit per change. Can I upload multiple commits to my PR?

You can upload as many commits as you like. GerritBot will handle squashing your commits into one change that Gerrit can handle.

### How does GerritBot determine the final commit message?

It uses the title and description of the PR to construct the commit message for the Gerrit Change.

### I need a Google account to sign up for Gerrit? Why can't I sign in using my GitHub account?

This is a limitation of the infrastructure that runs our Gerrit instances and is out of our control, plus you already need a Google account to sign our CLA, a requirement for us to accept your contribution in the first place.

### I left a reply to a comment in Gerrit but no one but me can see it

Replies to comments on code in Gerrit are first saved as drafts and need to be published via the “Reply” button. This is to prevent multiple emails per review “session” and is similar to the [pending review workflow](https://help.github.com/articles/reviewing-proposed-changes-in-a-pull-request/) in GitHub. If you see a number next to the “Reply” text in the button, this means you have pending drafts to publish.

## I'd like to add a feature/fix a bug

+ If the feature/bug is non-trivial, please [file an issue](https://github.com/golang/go/issues/new?title=x%2Fbuild%2Fcmd%2Fgerritbot%3A%20%3Cfill%20this%20in%3E) first
+ The code is located at x/build/cmd/gerritbot
  ([GitHub](https://github.com/golang/build/tree/master/cmd/gerritbot),
  [Gerrit](https://go.googlesource.com/build/+/master/cmd/gerritbot/))