---
title: CreatingSubRepository
---

This page outlines the steps that need to be done to create a new golang.org/x repository, in order for it to have the same properties as all existing golang.org/x repositories:

- a golang.org/x redirect
- automatic git mirroring from Gerrit to GitHub
- automatic importing of GitHub PRs into Gerrit CLs
- automatic testing on appropriate Go builders

## Steps

1. Create a new empty Gerrit repository at https://go.googlesource.com, complete with a description.
   - Create an initial commit with `LICENSE`, `PATENTS`, `CONTRIBUTING.md`, and `README.md` files and push it directly to the Gerrit repository. See [example commit](https://go.googlesource.com/govulncheck-action/+/a197ae39e55573b3a0e752b9bd72f457a458adf6).
   - See the internal team instructions at go/go-gerrit#new-repository for how to create a repository.
2. Create a [new empty GitHub repository](https://github.com/organizations/golang/repositories/new) at https://github.com/golang with the same name and description.
   - Turn off Wikis, Issues, Projects in repository settings.
   - On "Manage access" tab:
     - Add "golang org admins" team with Admin access.
     - Add "google-go-team" team with Write access.
     - Add "robots" team with Write access (can only be done by a maintainer of golang organization; ask someone else if you're not).
3. Modify the [`x/build/repos`](https://golang.org/x/build/repos) package.
   - Also modify the [`x/build/devapp/owners`](https://dev.golang.org/owners) to include the owner(s) of the new repository. (Both can be updated in one CL.)
4. Modify the [`PROJECTS` map](https://cs.opensource.google/go/x/build/+/luci-config:main.star;l=644-675;drc=67d27da0c4496ee84405c96517dfdaaf4e960cfc) on [luci-config](https://cs.opensource.google/go/x/build/+/luci-config:README) branch.
5. Update x/website's version of x/build to include modified `x/build/repos` package.
   - `x/website/cmd/golangorg` will [deploy automatically](https://go.googlesource.com/website#deploying) on CL submission.
6. Redeploy all affected commands (or ask an x/build [owner](https://dev.golang.org/owners) to deploy if you're not; the order shouldn't matter):
   1. `x/build/cmd/gitmirror`
   2. `x/build/maintner/maintnerd`
      - Note that it's expected for the new repo not to appear in maintner until first issue or PR is created (see [#25744](https://go.dev/issue/25744)).
   3. `x/build/cmd/gerritbot`
   4. `x/build/devapp`
7. You're done.
