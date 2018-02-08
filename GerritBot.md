GerritBot is a tool used for importing GitHub Pull Requests (PRs) into Gerrit for code review.

## Workflow

+ A user can upload a PR against any of our GitHub repos just as they would with any other GitHub project that accepts PRs
+ The PR changes will then be imported by GerritBot and a message will be posted to the GitHub PR Issue containing a link to the issue
+ All comments are handled within Gerrit. Any comments on the GitHub PR will be ignored
+ The PR author can continue to upload commits to the branch used by the PR in order to address feedback from Gerrit
+ Once the code is ready to be merged, a maintainer will submit the change on Gerrit and GerritBot will close the issue
+ Similarly, if a change is closed or abandoned on Gerrit, the corresponding PR will be closed

## Frequently Asked Questions

### Why is GerritBot the owner of my change?

This is due to an [open bug](https://bugs.chromium.org/p/gerrit/issues/detail?id=8296) with the way Gerrit handles acting as another user. Once that is fixed, the original author will also be the owner of the change.
 
### I heard Gerrit requires one commit per change. Can I upload multiple commits to my PR?

You can upload as many commits as you like. GerritBot will handle squashing your commits into one change that Gerrit can handle.

### How does GerritBot determine the final commit message?

It uses the title and description of the PR to construct the commit message for the Gerrit Change.

### I need a Google account to sign up for Gerrit? Why can't I sign in using my GitHub account?

This is a limitation of the infrastructure that runs our Gerrit instances and is out of our control, plus you you already need a Google account to sign our CLA, a requirement for us to accept your contribution in the first place.