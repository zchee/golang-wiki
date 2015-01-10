Be sure to familiarize yourself with the [code review process](http://golang.org/doc/contribute.html#Code_review) from the official Contribution Guidelines first.

# Reviewer Parlance

There are several terms code reviews may use that you should become familiar with.

  * ` LGTM ` — looks good to me
  * ` SGTM ` — sounds good to me
  * ` s/foo/bar/ ` — please replace ` foo ` with ` bar `; this is [sed syntax](http://en.wikipedia.org/wiki/Sed#Usage).
  * ` s/foo/bar/g ` — please replace ` foo ` with ` bar ` throughout your entire change

# Email

Messages from a code review are typically sent to three places:
  * the reviewers, if any
  * the golang-codereviews group
  * the owner

Please do NOT reply code review via email, as the message [will not be relayed to Gerrit](https://code.google.com/p/gerrit/issues/detail?id=228). Always click on the link and post reply in Gerrit.

# Code Review on Windows

The code review command ```git-codereview``` currently does not work on Windows. This is [#9257](../issues/9257).