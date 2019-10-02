This respository is home two to major versions of HCL: the original
implementation HCL 1, and the later reworking of it HCL 2.

In order to minimize problems for dependent codebases that are not yet using
Go Modules, for the moment our `master` branch refers to HCL 1, while HCL 2
development is ongoing in the branch [`hcl2`](https://github.com/hashicorp/hcl/tree/hcl2).

We recommend that all new projects that are considering using HCL should use
HCL 2. It has a more robust parser capable of producing better error messages,
a better architecture for parsing JSON as HCL, and incorporates an expression
language that was previously separated in the related codebase
[HIL](https://github.com/hashicorp/hil).

To use HCL 2 in your project, use [Go Modules](https://github.com/golang/go/wiki/Modules)
in your project select the latest HCL 2 release as follows:

```
go get github.com/hashicorp/hcl/v2
```

The `/v2` suffix on the module path above will cause the Go toolchain to select
the latest release from major version 2.

To install HCL 1 using Go Modules, use a module path with no version suffix:

```
go get github.com/hashicorp/hcl
```

This will select the latest release of major version 1. If you are using
Go Modules mode, you can safely depend on both major versions of HCL at the
same time in your project, in case you wish to migrate from HCL 1 to HCL 2.

If your project is _not_ using Go Modules mode, the Go toolchain will only be
able to select the latest commit from the `master` branch, which is HCL 1
currently. There is no way to automatically install HCL 2 in "`GOPATH` mode".

Until Go Modules is no longer experimental and is enabled by default in the Go
toolchain, we intend to leave the `master` branch pointed at the latest
development of _HCL 1_ so that existing callers not yet using Go Modules are
able to import it as before. However **we do intend to break this eventually**
by moving HCL 2 development into the `master` branch.

----

**We strongly recommend using either Go Modules or a legacy Go dependency vendoring tool to select and pin to the specific release of HCL 1 you need, rather than relying on the `master` branch.**

If you use `GOPATH` mode to select the `master` branch directly, you will see a breaking change at some later point when the `master` branch switches to being HCL 2.

----

## Contributing

If you wish to contribute to HCL 2, please be sure to set the base branch of
any PR you open to `hcl2` rather than `master` to ensure that the patch is
presented against the correct base.

HCL 1 is now in maintenence mode and we are unlikely to accept any new feature
requests or implementations into that version. For compatibility reasons, we
also don't intend to address any parser or decoder bugs that would change
behavior for existing applications depending on HCL 1. Our sole focus for
ongoing HCL 1 development will be severe bugs such as crashes.

Once Go Modules is no longer experimental, we will consider moving HCL 2
development into the `master` branch for a smoother contributor experience.
Sorry for the inconvenience of this unusual configuration in the meantime.
