Be sure to familiarize yourself with the [code review process](http://golang.org/doc/contribute.html#Code_review) from the official Contribution Guidelines first.

# Reviewer Parlance

There are several terms code reviews may use that you should become familiar with.

  * ` LGTM ` — looks good to me: the reviewer approves of your changes as they currently are. The reviewer may suggest minor changes; if so, you can make those changes, and then submit.
  * ` NOT LGTM ` — does not look good to me: the reviewer disapproves of your changes entirely. The reviewer will explain why they disapprove of your changes.
  * ` SGTM ` — sounds good to me: the reviewer approves of an idea mentioned in the review, but does not approve the changes for commit at this point.
  * ` s/foo/bar/ ` — The reviewer has requested that you replace the text ` foo ` with ` bar ` where they have commented. This notation originates from [sed syntax](http://en.wikipedia.org/wiki/Sed#Usage).
  * ` s/foo/bar/g ` — The reviewer has requested that you replace the text ` foo ` with ` bar ` throughout your entire change. This notation originates from [sed syntax](http://en.wikipedia.org/wiki/Sed#Usage).
  * ` CC=person ` — The reviewer has requested that ` person ` receive a copy of this review. This often originates from the [Go development dashboard](http://go-dev.appspot.com/).
  * ` R=person ` — The reviewer has requested for ` person ` to review this code before it is committed. This often originates from the [Go development dashboard](http://go-dev.appspot.com/).
  * ` R=close ` — The reviewer has requested that you close the review for now. They will explain why they wish for you to close the review.
  * ` TBR=person ` — This does not appear in code reviews themselves, but may appear in commit messages.  In this case, the committer has requested that ` person ` review this code as soon as possible, but the change is considered acceptable to be committed immediately.

# Email

Messages from a code review are typically sent to three places:
  * the reviewers, if any
  * the golang-codereviews group
  * the owner

Please do NOT reply code review via email, as the message will not be relayed to Gerrit. Always click on the link and post reply in Gerrit.

# Code Review on Windows

The code review command ```git-review``` currently does not work on Windows. This is [#9257](../issues/9257).