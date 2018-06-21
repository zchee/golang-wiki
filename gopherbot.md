This page outlines all interactive gopherbot functionality. Most of the tasks gopherbot performs do not require human intervention, however it is starting to learn new tricks.

## Adding/Removing Labels

You may add or remove labels by telling gopherbot what you'd like to do.

`@gopherbot, please add labels NeedsFix,help wanted and remove label needsinvestigation`

The comma after @gopherbot and the `please`, `and`, `add`, and `label[s]` keywords are optional. Adding a label is the default, so you can have the command be much more terse if you wish.

`@gopherbot needsfix, help wanted remove needsinvestigation`

The above command will achieve the same results as the first command.

If you don't wish to remove anything, you can omit the `remove` keyword.

`@gopherbot needsfix, help wanted`

The above command will add the `NeedsFix` and `help wanted` labels. Notice how labels must be separated by a comma (or semicolon). This is to account for those with spaces in them like `help wanted`. You cannot quote the labels.

`@gopherbot needsfix "help wanted"` **← Does not work**

Casing also doesn't matter. `needsfix` is equivalent to `NeedsFix`. gopherbot will figure out the right label for you.

There are some labels that are not allowed to be added or removed. Those can be seen in the `labelChangeBlacklisted` function in the [source](https://github.com/golang/build/blob/master/cmd/gopherbot/gopherbot.go).

For more in-depth examples, take a look at the [tests](https://github.com/golang/build/blob/master/cmd/gopherbot/gopherbot_test.go).

As always, patches are welcome!

## Backporting issues

gopherbot is capable of opening backport issues according to [MinorReleases](https://golang.org/wiki/MinorReleases) in response to comments like the following on the main issue.

> @gopherbot please consider this for backport to 1.10, it's a regression.

> @gopherbot please open the backport tracking issues. This is a severe compiler bug.

The keywords are `@gopherbot`, `backport`, `please` and optionally the release. They can be anywhere in the comment. If no release is mentioned issues are opened for the two past releases. The entire message is quoted in the new issue, so please include a rationale.

(Note that currently only the first backport command on an issue is executed. https://golang.org/issues/25574)