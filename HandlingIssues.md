This document explains how we handle issue triage and scheduling in [the Go project's issue tracker](http://golang.org/issue).

# New issues

All new issues are created with status "New" and no other labels.

When an issue is changed from "New" to "Accepted" (or any open state):
  * Mark it with a Release-**label (see below).
  * Add a sentence that describes the rationale for the label.**

If you're a committer creating an issue, you can change it from “New” to “Accepted” while filing the issue, but if you do, be sure to add a Release-**label and a rationale.**

# Release Labels

Any issue planned for a specific release (or explicitly not planned for a release) must have one of these labels:

  * Release-Go1.3 - must be addressed (and probably fixed) for Go 1.3
  * Release-Go1.3Maybe - would be nice if it were addressed for Go 1.3
  * Release-Go1.4 - will be re-examined for the next release
  * Release-None - no plan to fix in any specific release

# Dashboards

  * [Status-New](http://research.swtch.com/dashboard/Status-New)

  * [Release-Go1.3](http://research.swtch.com/dashboard/Go1.3)
  * [Release-Go1.4](http://research.swtch.com/dashboard/Go1.4)
  * [Release-None](http://research.swtch.com/dashboard/Release-None)

# Nominating an issue

If you're not a committer and you would like an issue to be addressed in Go 1.3, please:
  * Leave a comment on the issue explaining why,
  * Include the hashtag "#go13" in the comment.
Committers were periodically look at the issues with #go13 comments and adjust their status accordingly.