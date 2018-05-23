# VGO User Guide

vgo adds package version support to the Go tool chain. vgo will be present in the go1.11 go command as an opt-in feature.

## Installing

Until go1.11 comes out, install vgo with `go get -u golang.org/x/vgo`. To use, replace all uses of `go` with `vgo` so `go build` becomes `vgo build`.

## New Concepts

### Major Versions

Go modules must be released with semver in the form of `v(major).(minor).(patch)`. For example `v0.1.0`, `v1.2.3`, or `v3.0.1`. If using github, release a version with a tag. Distributed module repositories that are stand-alone will be coming in the future (they are being built right now).

The major version of a module must be included in both the module path and the package import path if the major version is v2 or higher. Module versions of v1 and v0 must not be included in the path. Modules with different paths are different modules. Thus `me.io/mymod` is different then `me.io/mymod/v2` and may import packages from one major version to another major version.

### Modules

Go packages now live in modules. Each module is associated with the URL path it may be found at and may include a major version at the end of the module path (but nowhere else). Modules may live outside of the `GOPATH`. Two example modules are `rsc.io/goversion` and `github.com/kardianos/vtest/v3`.

Modules are defined by a `go.mod` file that lives in the root of the module. Module files may include comments and will look familiar to a go programmer. Here is an example `go.mod` file:
```
module github.com/kardianos/vmain/v3

require (
    github.com/kardianos/vtest/v2 v2.0.2
)
```

There are 4 directives: "module", "require", "exclude", "replace". Module paths may be quoted but are not required to be.

Including major versions in import paths will produce incompatibilities with old versions of Go. To work around this prior versions of the go tool will be updated and released to continue building as before. Issue [25069](https://github.com/golang/go/issues/25069) tracks this.

Exclude and replace directives only operate on the current modules. Other packages that import a module that contains those directives will ignore them.

TODO: show example exclude and replace directives.

There are three ways to release a v2 (or higher) module version.
 1. Create a `v2` directory and place a new `go.mod` file in that folder. The module path must end with `/v2`. Tag the release with `v2.0.0`.
 2. Create a new branch, update the `go.mod` file to include a `/v2` at the end of the module path. Tag the release with `v2.0.0`.
 3. Update the `go.mod` file to include a `/v2` at the end of the module path. Tag the release with `v2.0.0`.

Packages are imported as normal with `import "me.io/mymod/v2/pkg1"` for a v2 package, or `import "me.io/mymod/pkg1"` for a v1 or v0 module.

### Version Solving

The version chosen to build is always one of the versions the module, or one of its dependencies. The version selected is the highest version of the chosen versions. This effectively locks versions into place until the module author chooses a new version to use. Use `go list -m` to list selected module versions.

Different major versions are effectively different modules. A `/v2` module will never be compared with a `/v3` module, even if the rest of the module path is the same. Only a single module will be included in a build at a time. This means `me.io/mymod` will only be included once, but `me.io/mymod/v2` may also be included.

### modverify

To verify the integrity of a module, create a new empty file called `go.modverify`.

## Setup

### New Modules

For new modules create a new file in the module root called `go.mod`. Edit it:
```
module github.com/user/modulename
```

You're ready to go.

### Existing Modules

If an existing module contains a `dep` lock file, it will be read and converted automatically on the first build. A new `go.mod` file will be written will use the versions found in the existing lock file.

If you put an empty `go.mod` file it will ignore any existing lock file and get the latest version of each dependency.

### Updating Dependencies

To update dependencies to the latest version, run `vgo get -u`.
