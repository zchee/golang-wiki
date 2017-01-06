# Gardening

## What is gardening?

"Gardening" in open source projects refers to the background maintenance tasks done to keep the project healthy & growing & nice looking.

This page lists common Go gardening tasks.

## Triage new bugs

Look at the untriaged bugs. For Go, we use the presence of a Milestone field to mean that the bug has been triaged. To search for un-milestoned issues, use https://github.com/golang/go/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+no%3Amilestone

While triaging the bug:

* is it a duplicate? Close it, referencing the dup.
* is it a Question rather than a bug? Close it and reply with something like "For questions about Go, see https://golang.org/wiki/Questions." 
* is the subject the correct format? It start with the package name and a colon, "net/http: fix crash in Server during foo operation"
* is it in a subrepo? Set the milestone to "Unreleased". Unless it's a subrepo that goes into a release, like godoc or http2.

## WaitingForReply

Find bugs that are in state WaitingForReply (https://github.com/golang/go/labels/WaitingForInfo) and ping them, remove the label when replies arrive, or close the bugs if a reply never arrived.

## Pending CLs

Review the format of commit messages and presence of tests and formatting of code and typos/grammar in incoming pending CLs. All of that can be done without determining the correctness of the change itself. See  https://dev.golang.org/release for the list of pending CLs.

