# SlowBots

The Go build system now supports "SlowBots", which are a way to configure the TryBots (pre-submit builders) to add additional builders into the set of build configurations that TryBots normally run.

Normally TryBots only run things that are fast and elastically provisioned. That is, TryBots only run x86 things that run on Google Cloud where we have tons of capacity and can spin up many VMs at will, sharding out test execution widely so the TryBots complete in 5-10 minutes.

But sometimes that's not enough. SlowBots let you say that you're cool waiting a long time until some specific set of builders becomes available. (There is often only one physical machine for some configurations, and often backlogged with work, and that builder might be slow too.)

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
* `specific-builder-name` (you specify it explicitly by its exact name; see the full list at https://farmer.golang.org/builders)
* `ios` (alias for `darwin-arm64`)

For the main Go repository, the terms after `TRY=` can also be:

* `x/repo`, where `repo` is one of the golang.org/x repositories whose tests should be executed. This runs a default builder for the given repo (`linux-amd64` as of writing).
* `x/repo@builder`, where `repo` is as above, and `builder` is a builder name from the [builder list](https://farmer.golang.org/builders). This runs the specified builder for the given repo. For example, `x/sys@linux-arm64-aws`.

When running TryBots again later, the most recent `TRY=` comment on the current patchset is used. To turn it off set `TRY=` with an empty string after the equals sign. If the current patchset doesn't have a `TRY=` comment, the most recent non-empty `TRY=` comment is used.

## Pitfalls

* `TRY=` comments are ignored if they're not on the same comment that started the TryBots
* TryBots (and SlowBots) don't run if there's already a TryBot-Result
* The `git-codereview mail` tool's `-trybot` flag doesn't support this yet, so use the web UI.
* If TryBots are already running, deleting the `Run-TryBot+1` vote and re-doing it won't re-start the TryBot set, so it won't look at your TRY= line, until the next run when it's done. (But you'll need to delete the TryBot-Result somehow: manually, rebasing, uploading new version)
* If you select a builder that's offline, it'll currently just wait forever for it to show up. There's no timeout yet.
* If you specify an unknown `TRY=` token, it'll just ignore it and won't report an error.
* There's no `all` alias. That's kinda intentional, to prevent overuse that might cause the SlowBots to get even slower for everybody. But we might add it later anyway. See [golang.org/issue/34501#issuecomment-544585711](https://go.dev/issue/34501#issuecomment-544585711).

## TODO

The usability of SlowBots will be improved over time. It needs to report things better, make it easier to configure (both CLI and probably a web GUI picker UI), and support restarting things, or modifying in-progress TryBot runs to change the set of builders. Feedback welcome at [golang.org/issue/34501](https://go.dev/issue/34501).