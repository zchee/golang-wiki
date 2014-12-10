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
  * the review itself
  * the golang-codereviews group
  * email

If you are replying to a review comment through email or the golang-codereviews group, you will notice two extra email addresses - golang-codereviews@googlegroups.com and reply@codereview-hr.appspotmail.com.  The former address ensures your message is posted to the golang-codereviews group, and the latter ensures your message is posted back to the review itself.  Keeping both of these on your replies makes sure your review message is visible everywhere.

# Code Review on Windows

The code review extension depends on Python modules that are not currently included in the standalone Mercurial installer for Windows. Attempting to use the code review extension will result in a "` *** failed to import extension codereview `" error.

## Option 1: Source Installation

To ensure that your Mercurial installation is compatible with the code review plugin, the "source install" package should be used instead of the standalone installer. The process to do this is as follows:

  * Check the Mercurial download page to determine the required Python version.
  * Install Python using the Windows installer from the Python download page.
  * Install Mercurial using the "Mercurial X.XX for Python X.X on Windows (source install)" installer from the Mercurial download page.
  * Update your ` PATH ` to include the Python installation directory and its ` scripts ` subdirectory.

## Option 2: Standalone Installation

If you would rather use the standalone Mercurial installer, it is possible to add the missing modules after completing the installation. You will need to copy files from the ` lib ` directory of an existing Python installation to the root directory of the ` library.zip ` file in the Mercurial installation directory. Depending on the version of Mercurial you have installed, the following files/directories may be needed:

  * the ` json/ ` subdirectory
  * ` htmlentitydefs.py `
  * ` HTMLParser.py `
  * ` markupbase.py `

# Dealing with Conflicts

When I run ` hg clpatch NNNN `, I get "patch and recent changes conflict". What do I do?

## Option 1: clpatch the old revision, use hg to merge

```
hg clp NNNN
# look at the revision that CL is against; call that revision AAAA
hg up AAAA
hg clp --no_incoming NNNN
hg up
# fix the merge conflicts, if any
# optionally, upload the merged revision:
hg upl NNNN
```

## Option 2: Apply the diff from the codereview website

Visit ` https://codereview.appspot.com/NNNN/ ` and note the raw diff url. It'll likely be something like ` https://codereview.appspot.com/download/issueNNNN_X0001.diff `.

```
# clpatch to bring in the CL metadata
hg clpatch --ignore_hgapplydiff_failure NNNN
# apply the diff
hg import --no-commit --force DIFF_URL
# fix the tree
# optionally, upload the merged revision:
hg upl NNNN
```

# Reverting local changes

You've run ` hg clpatch NNNN `, and you want to restore your repo to a clean state.

```
# Revert file changes.
hg revert @NNNN
# Remove local CL metadata.
hg change -D NNNN
# Remove added files. DANGER: Will delete *all* untracked files.
hg purge
```

# Submitting

If you were just given submit access, congrats. Some tips:

  * To check that you do in fact have submit access, go to any issue and click to enter a comment. If you have submit access, you'll notice a lot of extra options available beyond just commenting.
  * To submit, you'll need to configure mercurial to authorize with code.google.com. You can do this via the ` .hgrc ` auth section. Sample:
```
[auth]
go.prefix = https://code.google.com/p/go
go.username = *****@****.com
go.password = **********
```
  * By default, the password used for code.google.com is **not** your regular Google account password; visit https://code.google.com/hosting/settings.