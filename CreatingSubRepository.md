This page outlines the steps that need to be done to create a new golang.org/x repository, in order for it to have the same properties as all existing golang.org/x repositories:
- a golang.org/x redirect
- automatic git mirroring from Gerrit to GitHub
- automatic importing of GitHub PRs into Gerrit CLs

## Steps

1. Create a new empty Gerrit repository at https://go.googlesource.com, complete with a description.
2. Create a new empty GitHub repository at https://github.com/golang with the same name and description.
	- Turn off Wikis, Issues, Projects in repository settings.
	- On "Collaborators & teams" tab:
		- Add "golang org admins" team with Admin access.
		- Add "gophers" team with Write access.
		- Add "robots" team with Write access (can only be done by a maintainer of golang organization; ask someone else if you're not).
	- Create "cla: yes" and "cla: no" labels, they need to exist so that [@googlebot](https://github.com/googlebot) can automatically apply them. (Without a "cla: yes" label, PRs won't be imported into Gerrit.)
3. Modify 3 x/build commands:
	- In `cmd/gitmirror`, add the new repo to `shouldMirror` function.
	- In `maintner/maintnerd`, add the new repo to `goGitHubProjects` slice.
	- In `cmd/gerritbot`, add the new repo to `gerritProjectWhitelist` map.
	- See [an example CL](https://golang.org/cl/133896) for all 3 changes.
4. Modify 1 x/website command:
	- In `cmd/golangorg`, add the new repo to `xMap` map.
		- See [an example CL](https://golang.org/cl/160137).
5. Redeploy all affected commands in the following order:
	1. `cmd/gitmirror` first
	2. `maintner/maintnerd` second
		- Note that it's expected for the new repo not to appear in maintner until first issue or PR is created (see [#25744](https://golang.org/issue/25744)).
	3. `cmd/gerritbot` third
	4. `cmd/golangorg` fourth