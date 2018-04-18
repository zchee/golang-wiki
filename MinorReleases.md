Fixes for regressions, security issues, and serious problems with no workaround are backported to the two supported major releases. For example a fix developed during the 1.11 cycle will be backported to a 1.9.x (if applicable) and 1.10.x release.

As soon as an interested party thinks an issue should be considered for backport, they open one or two “child” issues titled like `package: title [1.9 backport]`. The issue should include a link to the original issue, the CLs that need to be cherry-picked, and a short rationale about why the backport might be needed. [This will soon be automated via GopherBot](https://github.com/golang/go/issues/24899) but for now must be done manually.

The fix is developed for the main issue, which is closed when it’s merged to the master branch.

The child issue is assigned to the minor release milestone, is labeled **CherryPickCandidate**, and its candidacy is discussed there. Once it’s approved it transitions to **CherryPickApproved**. OSP team members and/or code owners approve cherry-picks via an informal process.

The original change author submits a cherry-pick change immediately against the release branch, and gets it merged with the approval of the OSP. This closes the child issue. Gerrit is configured to restrict submissions to the release branches to CLs with a +2 from a member of the OSP.

At release time, any open backport issue which is not release-blocker is pushed to the next minor release milestone, and a minor release is minted with the already merged changes.

## Security releases

Security releases preempt the next minor release and need to ship only the security fix.

To avoid rolling back the release branch in that exceptional case, a new release branch is created based on the previous release. For example `release-branch.go1.9.5` is branched from tag `go1.9.4`. The release is tagged from that branch, and the branch is then merged into the main release branch. For example `release-branch.go1.9.5` is merged into `release-branch.go1.9`.

