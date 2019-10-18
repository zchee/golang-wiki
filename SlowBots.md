# SlotBots

The Go build system now supports "SlowBots", which are a way to configure the TryBots (pre-submit builders) to add additional builders into the set of build configurations that TryBots normally run.

Normally TryBots only run things that are fast and elastically provisioned. That is, TryBots only run x86 things that run on Google Cloud where we have tons of capacity and can spin up many VMs at will, sharding out test execution widely so the TryBots complete in 5-10 minutes.

But sometimes that's not enough. SlowBots let you say that you're cool waiting a long time until some specific set of build configurations becomes available.

## Using SlowBots

* Use the Gerrit web UI to reply and select `Run-TryBot` = `+1` as normal, but...
* In the comment section (where it says _Say something nice..._), write a magic comment:

```
TRY=ppc64le, freebsd, netbsd-386, ios, linux-arm64-packet
```

... where the terms after `TRY=` are either:

* `GOOS` (picks best one)
* `GOARCH` (picks best one)
* `GOOS-GOARCH` (picks best one)
* `GOOS-GOARCH-specificbuilder` (you specify it, so it doesn't pick one)
* `ios` (alias for `darwin-arm64`)

We might add more aliases later.

## Pitfalls

* `TRY=` comments are ignored if they're not on the same comment that started the TryBots
* TryBots (and SlowBots) don't run if there's already a TryBot-Result
* The `git-codereview mail` tool's `-trybot` flag doesn't support this yet, so use the web UI.
* If TryBots are already running, deleting the `Run-TryBot+1` vote and re-doing it won't re-start the TryBot set, so it won't look at your TRY= line, until the next run when it's done. (But you'll need to delete the TryBot-Result somehow: manually, rebasing, uploading new version)

## TODO

Yes, the usability of SlowBots isn't great yet. It was added where it was most convenient. It needs to report things better, make it easier to configure (both CLI and probably a web GUI picker UI), and support restarting things, or modifying in-progress TryBot runs to change the set of builders. Feedback welcome at https://github.com/golang/go/issues/34501.

