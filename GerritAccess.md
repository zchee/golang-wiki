# Gerrit Access

There are two types of Gerrit access described here, with different powers & responsibilities. Only ask for access if you're an active member of the community. New contributors should participate in the Gerrit code review process for some time before requesting access.

(For Github access, see https://go.dev/wiki/GithubAccess)

## Becoming an Approver ("approvers")

Approvers can review and submit code changes (CLs), subject to the review rules described below. Being an approver comes with an expectation of responsibility: approvers are people who care about Go and want to help it succeed. An approver is not just someone who can make changes, but someone who has demonstrated their ability to collaborate with the team, get the most knowledgeable people to review code, contribute high-quality code, and follow through to fix issues (in code or tests). 

Every CL requires _both_ a code review (Code-Review+2) from an approver and the involvement of a second trusted approver (an additional Code-Review+2, or a Trust+1). Requiring two people ensures that code cannot be submitted unilaterally from a single compromised account. If the author of a change is an approver, they can provide the Trust+1 for their own CLs, but not the Code-Review+2. Once a review has a Code-Review+2 and either a second Code-Review+2 or a Trust+1, it can be submitted, by any approver. All these rules are enforced by the Gerrit server.

A Code-Review+2 vote means that you have read the change and are confident that it is correct and appropriate to submit. Typically, you should only Code-Review+2 code in directories or packages that you "own"; the exception is trivial and obviously correct changes. Note that all user-visible new features or changes—new API, new command-line flags, and so on—need to go through the [proposal process](https://go.dev/s/proposal-process). The CLs should reference the specific accepted proposal [in the commit message](https://github.com/golang/go/wiki/CommitMessage) (“For #NNN.”).

A Trust+1 vote means that you have read the change and are confident that the change does not introduce any sort of security vulnerability or other clearly inappropriate code change. As long as you are sure about that, it's OK to Trust+1 a change even if you don't fully understand all the details of the change.

When a change has the appropriate reviews to be submitted, a Submit button appears in Gerrit (for approvers). You should only submit changes with a Code-Review+2 from the owner of that area (maybe you!).

If you are an approver, you can (and are encouraged to) Trust+1 every change you mail, by changing your [`git mail` alias](https://go.dev/doc/contribute#git-config) to be `git codereview mail -trust`. 

To request approver access, reference https://go-review.googlesource.com/#/admin/groups/1005,members in your bug. See below.

As an exception to the usual rules, the usual approvers group does not have Code-Review and Trust voting ability in the x/website repo. There, those votes are limited to Go team members working at Google. This restriction exists for supply chain security reasons, because commits to x/website automatically go live on https://go.dev/, which serves Go binary downloads.

## Running TryBots ("may-start-trybots")

TryBot access lets you kick off a test run of a CL in Gerrit prior to submission (pre-submit testing). Every test run includes a default set of the most common builders, and [SlowBots](https://go.dev/wiki/SlowBots) provide additional testing controls.

TryBots run in a somewhat-secure and somewhat-isolated environment, but they're not perfectly security hardened. You must skim the CL for anything malicious before starting TryBots.

To request TryBot access, reference https://go-review.googlesource.com/#/admin/groups/1030,members in your bug. See below.

# Requesting Access

To get request either of the access types above, file a bug (https://github.com/golang/go/issues/new?title=access:+&body=See+https://go.dev/wiki/GerritAccess) and list and state which access you want (its name and group URL), and state your Gerrit email address.

Decisions about granting access are made by the Go release team at Google. If your request is declined, it is almost always because you haven't been active enough for them to get a clear enough signal about your work, understanding of project conventions, and so on. Don't lose heart: it can take time to reach that level of familiarity.

## Once you have access

Go help garden! See https://go.dev/wiki/Gardening.