# Gerrit Access

There are two types of Gerrit access described here, with different powers & responsibilities. Only ask for access if you're an active member of the community. New contributors should participate in the Gerrit code review process for some time before requesting access.

(For Github access, see https://golang.org/wiki/GithubAccess)

## Approver Access ("approvers")

Approver access gives you power to +2 CLs and submit them.

Rules for voting +2 on changes: only +2 things that you're very confident in, and generally only in a directory (or package) that you normally "own", unless it's trivial and obviously correct.

Rules for submitting changes: if a change touches an area that you own, you can submit any changes after a +2. But elsewhere only submit your own changes after receiving a +2 from the owner of that area.

Approver access also gives you power to Trust+1 CLs. Every code change requires two approvers, with at least one +2. The second approver can Trust+1 (a +2 from a second approver also suffices).

Rules for voting Trust+1 on changes: only Trust+1 a change if you are confident that the change does not introduce any sort of security vulnerability or other clearly inappropriate code change. As long as you are sure about that, it's OK to Trust+1 a change even if you don't fully understand all the details of the change.

If the author of the change is an approver, they may (and are expected to) Trust+1 their own change, but someone else must +2 the change before it can be submitted.

To request this access, reference https://go-review.googlesource.com/#/admin/groups/1005,members in your bug. See below.

## Trybot Access ("may-start-trybots")

Trybot access lets you kick off a trybot run, testing a CL in Gerrit against the most common builders. The Trybots run in a somewhat-secure and somewhat-isolated environment, but they're not perfectly security hardened. You must skim the CL for anything malicious before starting Trybots.

To request this access, reference https://go-review.googlesource.com/#/admin/groups/1030,members in your bug. See below.

# Requesting Access

To get request either of the access types above, file a bug (https://github.com/golang/go/issues/new?title=access:+&body=See+https://golang.org/wiki/GerritAccess) and list and state which access you want (its name and group URL), and state your Gerrit email address.

## Once you have access

Go help garden! See https://golang.org/wiki/Gardening.