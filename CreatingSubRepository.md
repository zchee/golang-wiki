This page outlines the steps that need to be done after a new subrepository is added to go.googlesource.com, in order for it to get mirrored to GitHub, set up PR to Gerrit importing, etc.:

- Create a new empty repository at https://github.com/golang with the same name, complete with a description.
	- Turn off Wikis, Issues in repository settings.
	- On "Collaborators & teams" tab:
		- Add "golang org admins" team with Admin access.
		- Add "gophers" team with Write access.
		- Add "robots" team with Write access (can only be done by a maintainer of golang organization; ask someone else if you're not).
	- Create "cla: yes" and "cla: no" labels, they need to exist so that [@googlebot](https://github.com/googlebot) can automatically apply them. (Without a "cla: yes" label, PRs won't be imported into Gerrit.)
- Modify 3 x/build commands:
	- In `cmd/gerritbot`, add the new repo to `gerritProjectWhitelist` map.
	- In `cmd/gitmirror`, add the new repo to `shouldMirror` function.
	- In `maintner/maintnerd`, add the new repo to `goGitHubProjects` slice.
	- See [an example commit](https://github.com/golang/build/commit/a196f5a8e8d347b6b9fe4cd225a3393a77c03214).
	- Redeploy all 3: `cmd/gitmirror` first, `maintner/maintnerd` second, `cmd/gerritbot` third.
		- Note that it's expected for the new repo not to appear in maintner until first issue or PR is created (see [#25744](https://golang.org/issue/25744)).