---
title: LUCI
---

LUCI is the CI infrastructure for the Go project. The primary post-submit dashboard can be found at https://ci.chromium.org/p/golang.

## TryBots

Voting Commit-Queue+1 asks CQ to run the CL on the TryBots.

When the TryBots finish, CQ will reply with results, \
voting either LUCI-TryBot-Result+1 (pass) or LUCI-TryBot-Result-1 (fail). \
Important results (e.g. failures) will also appear as chips at the top \
of the Gerrit page for the CL, under the commit message.

![A red box indicating the location of the checks under the commit
message on the Gerrit page for an example CL.](https://github.com/golang/go/assets/1248668/93267ff3-11cd-41f7-b268-a5cc342cfcd3)

More details about what was run are available at the "Checks" tab
on the Gerrit CL page.

![A red arrow pointing to the location of the checks tab on the
Gerrit page for an example CL.](https://github.com/golang/go/assets/1248668/1a11fa8c-14cd-4b97-968c-6c52a8634c51)

Every TryBot run includes a default set of the most common builders.
[SlowBots](https://go.dev/wiki/SlowBots) provide additional testing controls.

## Troubleshooting

### "infra failed" / purple failure

Builders that fail with "infra failed" have a purple chip rather than green (passed) or red (tests failed). These failures indicate some kind of failure in the CI infrastructure itself. They are unlikely to be due to something in your CL.

If you encounter such errors, you can reach out to [golang-dev](https://groups.google.com/g/golang-dev) for help investigating them. You may also try rerunning the build, which may succeed on a subsequent run depending on the cause of the infra failure.

### build details

The "Steps & Logs" section on a LUCI build page enumerates steps that were executed. Each step can be expanded to get to its logs, environment variables, and command line arguments. The "get go" step includes the output of `go env` from the Go toolchain used in the build.
