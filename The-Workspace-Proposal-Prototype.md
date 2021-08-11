# Overview

The [Workspace proposal](https://github.com/golang/go/issues/45713) aims to improve the workflow of developers who often make changes in multiple modules. If the proposal is accepted, developers no longer need to modify the `go.mod` file with replace directives that ultimately shouldn't be checked in, and to manage sets of replaces for each "root" module of their build. Further, `go.work` provides configuration for tools that intend to operate on multiple modules at the same time, for example `gopls`.

Please read the [Workflows](https://go.googlesource.com/proposal/+/master/design/45713-workspace.md#workflows) section of the Workspace proposal design document for more information about the workflows the proposal aims to address and how it addresses them. If you have a multi-module workflow that you'd like improved, please give feedback on the [proposal issue](#45713) on how the prototype does or does not help.

# Setting up the Go command

# Setting up `gopls`

# Known issues with the prototype
* Replace directives are not yet supported in the `go.work` file.
# Giving Feedback