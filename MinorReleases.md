Fixes for regressions, security issues, and serious problems with no workaround are backported to the two supported major releases. For example a fix developed during the 1.11 cycle will be backported to a 1.9.x (if applicable) and 1.10.x release.

As soon as an interested party thinks an issue should be considered for backport, they open one or two “child” issues titled like `package: title [1.9 backport]`. The issue should include a link to the original issue and a short rationale about why the backport might be needed.

GopherBot is capable of opening the backport issues automatically in response to comments like the following on the main issue. (The keywords are `@gopherbot`, `backport`, `please` and optionally the release. The entire message is quoted in the new issue.)

> @gopherbot please consider this for backport to 1.10, it's a regression.

> @gopherbot please open the backport tracking issues. This is a severe compiler bug.

The fix is developed for the main issue, which is closed when the fix is merged to the master branch.

The child issue is assigned to the minor release milestone and labeled **CherryPickCandidate**, and its candidacy is discussed there. Once it is approved it transitions to **CherryPickApproved**. Release managers (a subset of the Go team that handles the release process) and/or code owners approve cherry-picks via an informal process.

When the child issue is labeled **CherryPickApproved**, the original author of the change fixing
that issue should immediately [create and mail a cherry-pick change](#making-cherry-pick-cls) against the release branch, which will be merged as soon as it is ready, closing the child issue.

At release time, any open backport issue which is not release-blocker is pushed to the next minor release milestone, and a minor release is minted with the already merged changes.

## Making cherry-pick CLs

Once the main fix has been submitted to master, take note of its commit hash, then use `git codereview` and `git cherry-pick` to prepare a cherry-pick CL:

```
git codereview change release-branch.go1.10
git codereview change cherry-pick-NNNN
git cherry-pick $COMMIT_HASH
git commit --amend # add message prefix and change Fixes line
git codereview mail
```

The cherry-pick CL must include a message prefix like `[release-branch.go1.10]`, and update the "Fixes" line to the child issue. Do not change the "Change-Id" line.

Gerrit is configured to only allow release managers to submit to release branches, but the code review process is otherwise the usual.

## Security releases

Security releases preempt the next minor release and need to ship only the security fix.

To avoid rolling back the release branch in that exceptional case, a new release branch is created based on the previous release. For example `release-branch.go1.9.5` is branched from tag `go1.9.4`. The release is tagged from that branch, and the branch is then merged into the main release branch. For example `release-branch.go1.9.5` is merged into `release-branch.go1.9`.

