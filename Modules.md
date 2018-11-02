# Go 1.11 Modules

Go 1.11 includes preliminary support for versioned modules as proposed [here](https://golang.org/design/24301-versioned-go). Modules are an [experimental](https://research.swtch.com/vgo-accepted) opt-in feature in Go 1.11, with the hope of incorporating feedback and finalizing the feature for Go 1.12. Even though the details may change, future releases will support modules defined using Go 1.11 or `vgo`.

The recent work by the Go team on versioned modules started outside of the main Go repository with the `vgo` tool, but on July 12, 2018 support for versioned modules landed in the main repository ([announcement thread](https://groups.google.com/d/msg/golang-dev/a5PqQuBljF4/61QK4JdtBgAJ)), and [Go 1.11 was released](https://groups.google.com/d/msg/golang-nuts/-yv9VlfsFCg/lPX_DUJnEQAJ) on August 24, 2018.

Please provide feedback on modules via [existing or new issues](https://github.com/golang/go/wiki/Modules#github-issues) and via [experience reports](https://github.com/golang/go/wiki/ExperienceReports).

## Table of Contents

The remaining content on this page is organized as follows:
* [Quick Start Example](https://github.com/golang/go/wiki/Modules#quick-start-example)
* [New Concepts](https://github.com/golang/go/wiki/Modules#new-concepts)
   * [Modules](https://github.com/golang/go/wiki/Modules#modules)
   * [go.mod](https://github.com/golang/go/wiki/Modules#gomod)
   * [Version Selection](https://github.com/golang/go/wiki/Modules#version-selection)
   * [Semantic Import Versioning](https://github.com/golang/go/wiki/Modules#semantic-import-versioning)
* [How to Use Modules](https://github.com/golang/go/wiki/Modules#how-to-use-modules)
   * [How to Install and Activate Module Support](https://github.com/golang/go/wiki/Modules#how-to-install-and-activate-module-support)
   * [How to Define a Module](https://github.com/golang/go/wiki/Modules#how-to-define-a-module)
   * [How to Upgrade and Downgrade Dependencies](https://github.com/golang/go/wiki/Modules#how-to-upgrade-and-downgrade-dependencies)
   * [How to Prepare for a Release (All Versions)](https://github.com/golang/go/wiki/Modules#how-to-prepare-for-a-release)
   * [How to Prepare for a Release (v2 or Higher)](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher)
* [Additional Resources](https://github.com/golang/go/wiki/Modules#additional-resources)
* [Changes Since the Initial Vgo Proposal](https://github.com/golang/go/wiki/Modules#changes-since-the-initial-vgo-proposal)
* [GitHub Issues](https://github.com/golang/go/wiki/Modules#github-issues)
* [FAQs](https://github.com/golang/go/wiki/Modules#faqs)
  * [How are versions marked as incompatible?](https://github.com/golang/go/wiki/Modules#how-are-versions-marked-as-incompatible)
  * [When do I get old behavior vs. new module-based behavior?](https://github.com/golang/go/wiki/Modules#when-do-i-get-old-behavior-vs-new-module-based-behavior)
  * [Why does installing a tool via 'go get' fail with error 'cannot find main module'?](https://github.com/golang/go/wiki/Modules#why-does-installing-a-tool-via-go-get-fail-with-error-cannot-find-main-module)
  * [How can I track tool dependencies for a module?](https://github.com/golang/go/wiki/Modules#how-can-i-track-tool-dependencies-for-a-module)
  * [What is the status of module support in IDEs, editors and standard tools like goimports, gorename, etc.?](https://github.com/golang/go/wiki/Modules#what-is-the-status-of-module-support-in-ides-editors-and-standard-tools-like-goimports-gorename-etc)
* [FAQs — Additional Control](https://github.com/golang/go/wiki/Modules#faqs--additional-control)
  * [What community tooling exists for working with modules?](https://github.com/golang/go/wiki/Modules#what-community-tooling-exists-for-working-with-modules)
  * [When should I use the 'replace' directive?](https://github.com/golang/go/wiki/Modules#when-should-i-use-the-replace-directive)
  * [Can I work entirely outside of VCS on my local filesystem?](https://github.com/golang/go/wiki/Modules#can-i-work-entirely-outside-of-vcs-on-my-local-filesystem)
  * [How do I use vendoring with modules? Is vendoring going away?](https://github.com/golang/go/wiki/Modules#how-do-i-use-vendoring-with-modules-is-vendoring-going-away)
  * [Are there "always on" module repositories and enterprise proxies?](https://github.com/golang/go/wiki/Modules#are-there-always-on-module-repositories-and-enterprise-proxies)
  * [Can I control when go.mod gets updated and when the go tools use the network to satisfy dependencies?](https://github.com/golang/go/wiki/Modules#can-i-control-when-gomod-gets-updated-and-when-the-go-tools-use-the-network-to-satisfy-dependencies)
  * [How do I use modules with CI systems such as Travis or CircleCI?](https://github.com/golang/go/wiki/Modules#how-do-i-use-modules-with-ci-systems-such-as-travis-or-circleci)
* [FAQs — go.mod and go.sum](https://github.com/golang/go/wiki/Modules#faqs--gomod-and-gosum)
  * [Why does 'go mod tidy' record indirect and test dependencies in my 'go.mod'?](https://github.com/golang/go/wiki/Modules#why-does-go-mod-tidy-record-indirect-and-test-dependencies-in-my-gomod)
  * [Is 'go.sum' a lock file? Why does 'go.sum' include information for module versions I am no longer using?](https://github.com/golang/go/wiki/Modules/#is-gosum-a-lock-file-why-does-gosum-include-information-for-module-versions-i-am-no-longer-using)
  * [Should I still add a 'go.mod' file if I do not have any dependencies?](https://github.com/golang/go/wiki/Modules#should-i-still-add-a-gomod-file-if-i-do-not-have-any-dependencies)
  * [Should I commit my 'go.sum' file as well as my 'go.mod' file?](https://github.com/golang/go/wiki/Modules#should-i-commit-my-gosum-file-as-well-as-my-gomod-file)
* [FAQs — Semantic Import Versioning](https://github.com/golang/go/wiki/Modules#faqs--semantic-import-versioning)
  * [Why must major version numbers appear in import paths?](https://github.com/golang/go/wiki/Modules#why-must-major-version-numbers-appear-in-import-paths)
  * [Why are major versions v0, v1 omitted from import paths?](https://github.com/golang/go/wiki/Modules#why-are-major-versions-v0-v1-omitted-from-import-paths)
  * [What are some implications of tagging my project with major version v0, v1, or making breaking changes with v2+?](https://github.com/golang/go/wiki/Modules#what-are-some-implications-of-tagging-my-project-with-major-version-v0-v1-or-making-breaking-changes-with-v2)
* [FAQs — Minimal Version Selection](https://github.com/golang/go/wiki/Modules#faqs--minimal-version-selection)
  * [Won't minimal version selection keep developers from getting important updates?](https://github.com/golang/go/wiki/Modules#wont-minimal-version-selection-keep-developers-from-getting-important-updates)
* [FAQs — Possible Problems](https://github.com/golang/go/wiki/Modules#faqs-possible-problems)
  * [Why does 'go build' require gcc, and why are prebuilt packages such as net/http not used?](https://github.com/golang/go/wiki/Modules#why-does-go-build-require-gcc-and-why-are-prebuilt-packages-such-as-nethttp-not-used)
  * [Do modules work with relative imports like `import "./subdir"`?](https://github.com/golang/go/wiki/Modules#do-modules-work-with-relative-imports-like-import-subdir)
  * [Some needed files may not be present in populated vendor directory](https://github.com/golang/go/wiki/Modules#some-needed-files-may-not-be-present-in-populated-vendor-directory)
* [FAQs — Miscellaneous](https://github.com/golang/go/wiki/Modules#faqs--miscellaneous)
  * [How did the 'go mod' commands change in go1.11beta3?](https://github.com/golang/go/wiki/Modules#how-did-the-go-mod-commands-change-in-go111beta3)

## Quick Start Example

The details are covered in the remainder of this page, but here is a simple example of creating a module from scratch.

Create a directory outside of your GOPATH:
```
$ mkdir -p /tmp/scratchpad/hello
$ cd /tmp/scratchpad/hello
```

Initialize a new module:
```
$ go mod init github.com/you/hello

go: creating new go.mod: module github.com/you/hello
```

Write your code:
```
$ cat <<EOF > hello.go
package main

import (
    "fmt"
    "rsc.io/quote"
)

func main() {
    fmt.Println(quote.Hello())
}
EOF
```

Build and run:
```
$ go build 
$ ./hello

Hello, world.
```

Note your `go.mod` file includes explicit versions for your dependencies:
```
$ cat go.mod

module github.com/you/hello

require rsc.io/quote v1.5.2
```

## New Concepts

These sections provide a high-level introduction to the main new concepts. For more details and rationale, please see [the official proposal document](https://golang.org/design/24301-versioned-go), this 40-minute introductory [video by Russ Cox describing the philosophy behind the design](https://www.youtube.com/watch?v=F8nrpe0XWRg&list=PLq2Nv-Sh8EbbIjQgDzapOFeVfv5bGOoPE&index=3&t=0s), or the more detailed initial [vgo blog series](https://research.swtch.com/vgo).

### Modules

A *module* is a collection of related Go packages that are versioned together as a single unit. Most often, a single version-control repository corresponds exactly to a single module, but alternatively, a single version-control repository can hold multiple modules.

Modules record precise dependency requirements and create reproducible builds. 

Modules must be [semantically versioned](https://semver.org/) in the form `v(major).(minor).(patch)`, such as  `v0.1.0`, `v1.2.3`, or `v3.0.1`. The leading `v` is required. If using Git, [tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging) released commits with their versions. Public and private module repositories and proxies are becoming available (see for example FAQ [below](https://github.com/golang/go/wiki/Modules#are-there-always-on-module-repositories-and-enterprise-proxies)).

### go.mod

A module is defined by a tree of Go source files with a `go.mod` file in the tree's root directory. Module source code may be located outside of GOPATH.

`go.mod` files may include comments and will look familiar to a Go programmer. Here is an example `go.mod` file defining the module `github.com/my/thing`:

```
module github.com/my/thing

require (
    github.com/some/dependency v1.2.3
    github.com/another/dependency/v4 v4.0.0
)
```

There are four directives: `module`, `require`, `exclude`, `replace`. 

All of the packages in a module share a common prefix -- the *module path*. The `go.mod` file defines the module path via the `module` directive. For example, if you are defining a module for two packages `example.com/my/project/foo` and `example.com/my/project/bar`, the first line in your `go.mod` file typically would be `module example.com/my/project`, and the corresponding on-disk structure could be:

```
project/
├── go.mod
├── bar
│   └── bar.go
└── foo
    └── foo.go
```

`exclude` and `replace` directives only operate on the current (“main”) module. `exclude` and `replace` directives in modules other than the main module are ignored when building the main module. The `replace` and `exclude` statements therefore allow the main module complete control over its own build, without also being subject to complete control by dependencies.  (See FAQ [below](https://github.com/golang/go/wiki/Modules#when-should-i-use-the-replace-directive) for discussion of when to use a `replace` directive).

In Go source code, packages are imported using the full path including the module, for example:
 * `import "example.com/my/module/v2/pkg/foo"` to import `foo` from the v2 version of module `example.com/my/module`.

### Version Selection

If you add a new import to your source code that is not yet covered by a `require` in `go.mod`, any go command run (e.g., 'go build') will automatically look up the proper module and add the *highest* version of that new direct dependency to your module's `go.mod` as a `require` directive. For example, if your new import corresponds to dependency M whose latest tagged release version is `v1.2.3`, your module's `go.mod` will end up with `require M v1.2.3`, which indicates module M is a dependency with allowed version >= v1.2.3 (and < v2, given v2 is considered incompatible with v1).

The *minimal version selection* algorithm is used to select the versions of all modules used in a build. For each module in a build, the version selected by minimal version selection is always the semantically *highest* of the versions explicitly listed by a `require` directive in the main module or one of its dependencies. 

As an example, if your module depends on module A which has a `require D v1.0.0`, and your module also depends on module B which has a `require D v1.1.1`, then minimal version selection would choose `v1.1.1` of D to include in the build (given it is the highest listed `require` version). This selection of `v1.1.1` remains consistent even if some time later a `v1.2.0` of D becomes available. This is an example of how the modules system provides 100% reproducible builds. When ready, the module author or user might choose to upgrade to the latest available version of D or choose an explicit version for D. 

For a brief rationale and overview of the minimal version selection algorithm, [see the "High Fidelity Builds" section](https://github.com/golang/proposal/blob/master/design/24301-versioned-go.md#update-timing--high-fidelity-builds) of the official proposal, or see the [more detailed `vgo` blog series](https://research.swtch.com/vgo).

To see a list of the selected module versions (including indirect dependencies), use `go list -m all`.

See also the ["How to Upgrade and Downgrade Dependencies"](https://github.com/golang/go/wiki/Modules#how-to-upgrade-and-downgrade-dependencies) section below and the ["How are versions marked as incompatible?"](https://github.com/golang/go/wiki/Modules#how-are-versions-marked-as-incompatible) FAQ below.

### Semantic Import Versioning

For many years, the official Go FAQ has included this advice on package versioning:

> "Packages intended for public use should try to maintain backwards compatibility as they evolve. The Go 1 compatibility guidelines are a good reference here: don't remove exported names, encourage tagged composite literals, and so on. If different functionality is required, add a new name instead of changing an old one. If a complete break is required, create a new package with a new import path."

The last sentence is especially important — if you break compatibility, you should change the import path of your package. With Go 1.11 modules, that advice is formalized into the _import compatibility rule_:

> "If an old package and a new package have the same import path,
> the new package must be backwards compatible with the old package."

Recall [semantic versioning](https://semver.org/) requires a major version change when a v1 or higher package makes a backwards incompatible change. The result of following both the import compatibility rule and semantic versioning is called _semantic import versioning_, where the major version is included in the import path — this ensures the import path changes any time the major version increments due to a break in compatibility.

As a result of semantic import versioning, code opting in to Go modules **must comply with these rules**: 
* Follow [semantic versioning](https://semver.org/) (with tags such as `v1.2.3`).
* If the module is version v2 or higher, the major version of the module _must_ be included in both the module path in the `go.mod` file (e.g., `module example.com/my/mod/v2`) and the package import path (e.g., `import "example.com/my/mod/v2/foo"`).
* If the module is version v0 or v1, do _not_ include the major version in either the module path or the import path.

In general, packages with different import paths are different packages, including if different import paths are due to different major versions. Thus `example.com/my/mod/foo` is a different package than `example.com/my/mod/v2/foo`, and both may be imported in a single build, which among other benefits helps with diamond dependency problems and also allows a v1 module to be implemented in terms of its v2 replacement or vice versa.

One exception to the rules above is existing code that uses import paths starting with `gopkg.in` (such as `gopkg.in/yaml.v1` and `gopkg.in/yaml.v2`) can continue to use those forms for their module paths and import paths when opting in to modules.

See the ["Module compatibility and semantic versioning"](https://tip.golang.org/cmd/go/#hdr-Module_compatibility_and_semantic_versioning) section of the tip documentation for more details on semantic import versioning.

This section so far has been focused on code that opts in to modules. However, putting major versions in import paths for v2+ modules could create incompatibilities with older versions of Go, or with code that has not yet opted in to modules. To help with this, Go versions 1.9.7+, 1.10.3+ and 1.11 have been [updated](https://go-review.googlesource.com/c/go/+/109340)  so that code built with those releases can properly consume v2+ modules without requiring modification of pre-existing code. (When relying on this updated mechanism, a package that has _not_ opted in to modules would _not_ include the major version in the import path for any imported v2+ modules. In contrast, a package that _has_ opted in to modules _must_ include the major version in the import path for any imported v2+ modules).

For the exact mechanics required to release a v2+ module, please see the ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) section below.

## How to Use Modules

### How to Install and Activate Module Support

To use modules, two install options are:
* [Install the latest Go 1.11 release](https://golang.org/dl/).
* [Install the Go toolchain from source](https://golang.org/doc/install/source) on the `master` branch.

Once installed, you can then activate module support in one of two ways:
* Invoke the `go` command in a directory outside of the `$GOPATH/src` tree, with a valid `go.mod` file in the current directory or any parent of it and the environment variable `GO111MODULE` unset (or explicitly set to `auto`).
* Invoke the `go` command with `GO111MODULE=on` environment variable set.

### How to Define a Module

Most projects will follow the simplest approach of using a single module per repository, which typically would mean creating one `go.mod` file located in the root directory of a repository. (Multiple modules are supported in a single repository, but most often that would result in more work on an on-going basis than a single module per repository).

To create a `go.mod` for an existing project:

1. Navigate to the root of the module's source tree outside of GOPATH:

   ```
   $ cd <project path outside $GOPATH/src>         # e.g., cd ~/projects/hello
   ```
   Note that outside of GOPATH, you do not need to set `GO111MODULE` to activate module mode.

   Alternatively, if you want to work in your GOPATH:

   ```
   $ export GO111MODULE=on                         # manually active module mode
   $ cd $GOPATH/src/<project path>                 # e.g., cd $GOPATH/src/you/hello
   ```

2. Create the initial module definition and write it to the `go.mod` file:

   ```
   $ go mod init                  
   ```
   This step converts from any existing [`dep`](https://github.com/golang/dep) `Gopkg.lock` file or from any of the other [nine total supported dependency formats](https://tip.golang.org/pkg/cmd/go/internal/modconv/?m=all#pkg-variables), adding require statements to match the existing configuration.

   `go mod init` will often be able to use auxiliary data (such as VCS meta-data) to automatically determine the appropriate module path, but if `go mod init` states it can not automatically determine the module path, or if you need to otherwise override that path, you can supply the module path as follows:

   ```
   $ go mod init github.com/you/hello
   ```

3. Build the module. This will automatically add missing or unconverted dependencies as needed to satisfy imports for this particular build invocation:

   ```
   $ go build ./...
   ```
4. Test the module as configured to ensure that it works with the selected versions:

   ```
   $ go test ./...
   ```

5. (Optional) Run the tests for your module plus the tests for all direct and indirect dependencies to check for incompatibilities:

   ```
   $ go test all
   ```

Prior to tagging a release, see the ["How to Prepare for a Release"](https://github.com/golang/go/wiki/Modules#how-to-prepare-for-a-release) section below.

For more information on all of these topics, the primary entry point to the official modules documentation is [available on tip.golang.org](https://tip.golang.org/cmd/go/#hdr-Modules__module_versions__and_more).

## How to Upgrade and Downgrade Dependencies

Day-to-day adding, removing, upgrading, and downgrading of dependencies should be done using 'go get', which will automatically update the `go.mod` file.

In addition, go commands like 'go build', 'go test', or even 'go list' will automatically add new dependencies as needed to satisfy imports (updating `go.mod` and downloading the new dependencies).

To upgrade to the latest version for all transitive dependencies of the current module:
 * run `go get -u` to use the latest *minor or patch* releases
 * run `go get -u=patch` to use the latest *patch* releases

To upgrade or downgrade to a more specific version, 'go get' allows version selection to be overridden by adding an @version suffix or "module query" to the package argument, such as `go get github.com/gorilla/mux@v1.6.2`, `go get github.com/gorilla/mux@e3702bed2`, or `go get github.com/gorilla/mux@'<v1.6.2'`. 

`go get github.com/gorilla/mux` updates to the latest version with a [semver](https://semver.org/) tag. (This is  equivalent to `go get github.com/gorilla/mux@latest` — in other words, `@latest` is the default if no `@` version is specified).

Using a branch name such as `go get github.com/gorilla/mux@master` is one way to obtain the latest commit regardless of whether or not it has a semver tag.

In general, module queries that do not resolve to a semver tag will be recorded as [pseudo-versions](https://tip.golang.org/cmd/go/#hdr-Pseudo_versions) in the `go.mod` file.

Modules are capable of consuming packages that have not yet opted into modules. Modules can also consume packages that do not yet have any proper semver tags (in which case they will be recorded using pseudo-versions in `go.mod`).

See the ["Module-aware go get"](https://tip.golang.org/cmd/go/#hdr-Module_aware_go_get) and ["Module queries"](https://tip.golang.org/cmd/go/#hdr-Module_queries) sections of the tip documentation for more information on the topics here.

After upgrading or downgrading any dependencies, you may then want to run the tests again for all packages in your build (including direct and indirect dependencies) to check for incompatibilities:
   ```
   $ go test all
   ```

## How to Prepare for a Release

### Releasing Modules (All Versions)

Best practices for creating a release of a module are expected to emerge as part of the initial modules experiment. Many of these might end up being automated by a [future 'go release' tool](https://github.com/golang/go/issues/26420).

Some current suggested best practices to consider prior to tagging a release:

* Run `go mod tidy` to possibly prune any extraneous requirements (as described [here](https://tip.golang.org/cmd/go/#hdr-Maintaining_module_requirements)) and also ensure your current go.mod reflects all possible build tags/OS/architecture combinations (as described [here](https://github.com/golang/go/issues/25971#issuecomment-399091682)). 
  * In contrast, other commands like `go build` and `go test` will not remove dependencies from `go.mod` that are no longer required and only update `go.mod` based on the current build invocation's tags/OS/architecture.

* Run `go test all` to test your module (including running the tests for your direct and indirect dependencies) as a way of validating that the currently selected packages versions are compatible. 
  * The number of possible version combinations is exponential in the number of modules, so in general you cannot expect your dependencies to have tested against all possible combinations of their dependencies.
  * As part of the modules work, `go test all` has been [re-defined to be more useful](https://research.swtch.com/vgo-cmd) to include all the packages in the current module, plus all the packages they depend on through a sequence of one or more imports, while excluding packages that don't matter in the current module.

* Ensure your `go.sum` file is committed along with your `go.mod` file. See [FAQ below](https://github.com/golang/go/wiki/Modules#should-i-commit-my-gosum-file-as-well-as-my-gomod-file) for more details and rationale. 

### Releasing Modules (v2 or Higher)

If you are releasing a v2 or higher module, please first review the discussion in the ["Semantic Import Versioning" ](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above, which includes why major versions are included in the module path and import path for v2+ modules, as well as how Go versions 1.9.7+ and 1.10.3+ have been updated to simplify that transition.

There are two ways to release a v2 or higher module. Using the example of creating a `v3.0.0` release, the two options are:

1. **Major branch**: Update the `go.mod` file to include a `/v3` at the end of the module path in the `module` directive (e.g., `module github.com/my/module/v3`). Update import statements within the module to also use `/v3` (e.g., `import "github.com/my/module/v3/foo"`). Tag the release with `v3.0.0`. 
   * Go versions 1.9.7+, 1.10.3+, and 1.11 are able to properly consume and build a v2+ module created using this approach without requiring updates to consumer code that has not yet opted in to modules (as described in the the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above). 
   * A community tool [github.com/marwan-at-work/mod](https://github.com/marwan-at-work/mod) helps automate this procedure. See the [repository](https://github.com/marwan-at-work/mod) or the [community tooling FAQ](https://github.com/golang/go/wiki/Modules#what-community-tooling-exists-for-working-with-modules) below for an overview.
   * To avoid confusion with this approach, consider putting the `v3.*.*` commits for the module on a separate v3 branch.
   * If instead you have been previously releasing on master and would prefer to tag `v3.0.0` on master, that is a viable option, but consider creating a v1 branch for any future v1 bug fixes.

2. **Major subdirectory**: Create a new `v3` subdirectory (e.g., `my/module/v3`) and place a new `go.mod` file in that subdirectory. The module path must end with `/v3`. Copy or move the code into the `v3` subdirectory. Update import statements within the module to also use `/v3` (e.g., `import "github.com/my/module/v3/foo"`). Tag the release with `v3.0.0`.
   * This provides greater backwards compatibility. In particular, Go versions older than 1.9.7 and 1.10.3 are also able to properly consume and build a v2+ module created using this approach.

See https://research.swtch.com/vgo-module for a more in-depth discussion of these alternatives.

## Additional Resources

### Documentation and Proposal

* Official documentation:
  * Latest [HTML documentation for modules on tip.golang.org](https://tip.golang.org/cmd/go/#hdr-Modules__module_versions__and_more)
  * Run `go help modules` for more about modules. (This is the main entry point for modules topics via `go help`)
  * Run `go help mod` for more about the `go mod` command.
  * Run `go help module-get` for more about the behavior of `go get` when in module-aware mode.
  * Run `go help goproxy` for more about the module proxy, including a pure file-based option via a `file:///` URL.
* The initial ["Go & Versioning"](https://research.swtch.com/vgo) series of blog posts on `vgo` by Russ Cox (first posted February 20, 2018)
* Official [golang.org blog post introducing the proposal](https://blog.golang.org/versioning-proposal) (March 26, 2018)
  * This provides a more succinct overview of the proposal than the full `vgo` blog series, along with some of the history and process behind the proposal
* Official [Versioned Go Modules Proposal](https://golang.org/design/24301-versioned-go) (last updated March 20, 2018)

### Introductory Material

* Example based 35 minute introductory video ["What are Go modules and how do I use them?"](https://www.youtube.com/watch?v=6MbIzJmLz6Q&list=PL8QGElREVyDA2iDrPNeCe8B1u7li5S6ep&index=5&t=0s) ([slides](https://talks.godoc.org/github.com/myitcv/talks/2018-08-15-glug-modules/main.slide#1)) by Paul Jolly (August 15, 2018)
* Introductory blog post ["Taking Go Modules for a Spin"](https://dave.cheney.net/2018/07/14/taking-go-modules-for-a-spin) by Dave Cheney (July 14, 2018)
* Introductory [Go Meetup slides on modules](https://docs.google.com/presentation/d/1ansfXN8a_aVL-QuvQNY7xywnS78HE8aG7fPiITNQWMM/edit#slide=id.g3d87f3177d_0_0) by Chris Hines (July 16, 2018)
* Introductory 40 minute video ["The Principles of Versions in Go"](https://www.youtube.com/watch?v=F8nrpe0XWRg&list=PLq2Nv-Sh8EbbIjQgDzapOFeVfv5bGOoPE&index=3&t=0s) from GopherCon Singapore by Russ Cox (May 2, 2018)
  * Succinctly covers the philosophy behind the design of versioned Go modules, including the three core principles of "Compatibility", "Repeatability", and "Cooperation"

### Additional Material

* Blog post ["Using Go modules with vendor support on Travis CI"](https://arslan.io/2018/08/26/using-go-modules-with-vendor-support-on-travis-ci/) by Fatih Arslan (August 26, 2018)
* Blog post ["Go Modules and CircleCI"](https://medium.com/@toddkeech/go-modules-and-circleci-c0d6fac0b000) by Todd Keech (July 30, 2018)
* Blog post ["The vgo proposal is accepted. Now what?"](https://research.swtch.com/vgo-accepted) by Russ Cox (May 29, 2018)
  * Includes summary of what it means that versioned modules are currently an experimental opt-in feature
* Blog post on [how to build go from tip and start using go modules](https://carolynvanslyck.com/blog/2018/07/building-go-from-source/) by Carolyn Van Slyck (July 16, 2018)

## Changes Since the Initial Vgo Proposal

As part of the proposal, prototype, and beta processes, there have been over 400 issues created by the overall community. Please continue to supply feedback. 

Here is a partial list of some of the larger changes and improvements, almost all of which were primarily based on feedback from the community:

* Top-level vendor support was retained rather than vgo-based builds ignoring vendor directories entirely ([discussion](https://groups.google.com/d/msg/golang-dev/FTMScX1fsYk/uEUSjBAHAwAJ), [CL](https://go-review.googlesource.com/c/vgo/+/118316))
* Backported minimal module-awareness to allow older Go versions 1.9.7+ and 1.10.3+ to more easily consume modules for v2+ projects ([discussion](https://github.com/golang/go/issues/24301#issuecomment-371228742),  [CL](https://golang.org/cl/109340))
* Allowed vgo to use v2+ tags by default for pre-existing packages did not yet have a go.mod (recent update in related behavior described [here](https://github.com/golang/go/issues/25967#issuecomment-407567904))
* Added support via command `go get -u=patch` to update all transitive dependencies to the latest available patch-level versions on the same minor version ([discussion](https://research.swtch.com/vgo-cmd), [documentation](https://tip.golang.org/cmd/go/#hdr-Module_aware_go_get))
* Additional control via environmental variables (e.g., GOFLAGS in [#26585](https://github.com/golang/go/issues/26585), [CL](https://go-review.googlesource.com/c/go/+/126656))
* Finer grain control on whether or not go.mod is allowed to be updated, how vendor directory is used, and whether or not network access is allowed (e.g., -mod=readonly, -mod=vendor, GOPROXY=off; related [CL](https://go-review.googlesource.com/c/go/+/126696) for recent change)
* Added more flexible replace directives ([CL](https://go-review.googlesource.com/c/vgo/+/122400))
* Added additional ways to interrogate modules (for human consumption, as well as for better editor / IDE integration)
* The UX of the go CLI has continued to be refined based on experiences so far (e.g., [#26581](https://github.com/golang/go/issues/26581), [CL](https://go-review.googlesource.com/c/go/+/126655))
* Additional support for warming caches for use cases such as CI or docker builds via `go mod download` ([#26610](https://github.com/golang/go/issues/26610#issuecomment-408654653))
* **Most likely**: better support for installing specific versions of programs to GOBIN ([#24250](https://github.com/golang/go/issues/24250#issuecomment-377553022))

## GitHub Issues

* [Currently open module issues](https://golang.org/issues?q=is%3Aopen+is%3Aissue+label:modules)
* [Closed module issues](https://github.com/golang/go/issues?q=is%3Aclosed+is%3Aissue+label%3Amodules+sort%3Aupdated-desc)
* [Closed vgo issues](https://github.com/golang/go/issues?q=-label%3Amodules+vgo+is%3Aclosed+sort%3Aupdated-desc)
* Submit a [new module issue](https://github.com/golang/go/issues/new?title=cmd%2Fgo%3A%20%3Cfill%20this%20in%3E) using 'cmd/go:' as the prefix

## FAQs — Most Common

### How are versions marked as incompatible?

The `require` directive allows any module to declare that it should be built with version >= x.y.z of a dependency D (which may be specified due to  incompatibilities with version < x.y.z of module D). Empirical data suggests [this is the dominant form of constraints used in `dep` and `cargo`](https://twitter.com/_rsc/status/1022590868967116800). In addition, the top-level module in the build can `exclude` specific versions of dependencies or `replace` other modules with different code. See the full proposal for [more details and rationale](https://github.com/golang/proposal/blob/master/design/24301-versioned-go.md).

One of the key goals of the versioned modules proposal is to add a common vocabulary and semantics around versions of Go code for both tools and developers. This lays a foundation for future capabilities to declare additional forms of incompatibilities, such as possibly:
* declaring deprecated versions as [described](https://research.swtch.com/vgo-module) in the initial `vgo` blog series
* declaring pair-wise incompatibility between modules in an external system as discussed for example [here](https://github.com/golang/go/issues/24301#issuecomment-392111327) during the proposal process
* declaring pair-wise incompatible versions or insecure versions of a module after a release has been published. See for example the on-going discussion in [#24031](https://github.com/golang/go/issues/24031#issuecomment-407798552) and [#26829](https://github.com/golang/go/issues/26829)

### When do I get old behavior vs. new module-based behavior?

In general, modules are opt-in for Go 1.11, so by design old behavior is preserved by default.

Summarizing when you get the old 1.10 status quo behavior vs. the new opt-in modules-based behavior:

* Inside GOPATH — defaults to old 1.10 behavior (ignoring modules)
* Outside GOPATH while inside a file tree with a `go.mod` — defaults to modules behavior
* GO111MODULE environment variable:
  * unset or `auto` —  default behavior above
  * `on` —  force module support on regardless of directory location
  * `off` — force module support off regardless of directory location
 
### Why does installing a tool via `go get` fail with error `cannot find main module`?

This occurs when you have set `GO111MODULE=on`, but are not inside of a file tree with a `go.mod` when you run `go get`.

The simplest solution is to leave `GO111MODULE` unset (or equivalently explicitly set to `GO111MODULE=auto`), which avoids this error.

Recall one of the primary reason modules exist is to record precise dependency information. This dependency information is written to your current `go.mod`.  If you are not inside of a file tree with a `go.mod` but you have told the `go get` command to operate in module mode by setting `GO111MODULE=on`, then running `go get` will result in the error `cannot find main module` because there is no `go.mod` available to record dependency information.

Solution alternatives include:

1. Leave `GO111MODULE` unset (the default, or explicitly set `GO111MODULE=auto`), which results in friendlier behavior. This will give you Go 1.10 behavior when you are outside of a module and hence will avoid `go get` reporting `cannot find main module`.

2. Leave `GO111MODULE=on`, but as needed disable modules temporarily and enable Go 1.10 behavior during `go get`, such as via `GO111MODULE=off go get example.com/cmd`. This can be turned into a simple script or shell alias such as `alias oldget='GO111MODULE=off go get'`

3. Create a temporary `go.mod` file that is then discarded. This has been automated by a [simple shell script](https://gist.github.com/rogpeppe/7de05eef4dd774056e9cf175d8e6a168) by [@rogpeppe](https://github.com/rogpeppe). This script allows version information to optionally be supplied (usage: `vgoget example.com/cmd[@version]`).

4. Create a `go.mod` you use to track your globally installed tools, such as in `~/global-tools/go.mod`, and `cd` to that directory prior to running `go get` or `go install` for any globally installed tools. 

5. Create a `go.mod` for each tool in separate directories, such as `~/tools/gorename/go.mod` and `~/tools/goimports/go.mod`, and `cd` to that appropriate directory prior to running `go get` or `go install` for the tool. 

This current limitation will be resolved. However, the primary issue is that modules are currently opt-in, and a full solution will likely wait until GO111MODULE=on becomes the default behavior. See [#24250](https://github.com/golang/go/issues/24250#issuecomment-377553022) for more discussion, including this comment:

> This clearly must work eventually. The thing I'm not sure about is exactly what this does as far as the version is concerned: does it create a temporary module root and go.mod, do the install, and then throw it away? Probably. But I'm not completely sure, and for now I didn't want to confuse people by making vgo do things outside go.mod trees. Certainly the eventual go command integration has to support this.

This FAQ has been discussing tracking _globally_ installed tools.
 
If instead you want to track the tools required by a _specific_ module, see the next FAQ.

### How can I track tool dependencies for a module?

If you:
 *  want to use a go-based tool (e.g. stringer) while working on a module, and
 *  want to ensure that everyone is using the same version of that tool while tracking the tool's version in your module's `go.mod` file

then one currently recommended approach is to add a `tools.go` file to your module with a `// +build tools` build constraint as shown in [this comment in #25922](https://github.com/golang/go/issues/25922#issuecomment-412992431).

The brief rationale (also from #25922):

> I think the tools.go file is in fact the best practice for tool dependencies, certainly for Go 1.11.
> 
> I like it because it does not introduce new mechanisms.
> 
> It simply reuses existing ones.

### What is the status of module support in IDEs, editors and standard tools like goimports, gorename, etc?

Support for modules is starting to land in editors and IDEs. 

For example: 
* **GoLand**: currently has full support for modules outside and inside GOPATH, including completion, syntax analysis, refactoring, navigation as described [here](https://blog.jetbrains.com/go/2018/08/24/goland-2018-2-2-is-here/).
* **VS Code**: work is in progress and looking for contributors to help. Tracking issue is [#1532](https://github.com/Microsoft/vscode-go/issues/1532). An initial beta is described in the [VS Code module status wiki page](https://github.com/Microsoft/vscode-go/wiki/Go-modules-support-in-Visual-Studio-Code).
* **Atom with go-plus**: tracking issue is [#761](https://github.com/joefitzgerald/go-plus/issues/761).
* **vim with vim-go**: initial support for syntax highlighting and formatting `go.mod` has [landed](https://github.com/fatih/vim-go/pull/1931). Broader support tracked in [#1906](https://github.com/fatih/vim-go/issues/1906).
* **emacs with go-mode.el**: tracking issue in [#237](https://github.com/dominikh/go-mode.el/issues/237).

The status of other tools such as goimports, guru, gorename and similar tools is being tracked in an umbrella issue [#24661]( https://github.com/golang/go/issues/24661). Please see that umbrella issue for latest status.

Some tracking issues for particular tools includes:
* **gocode**: tracking issue in [mdempsky/gocode/#46](https://github.com/mdempsky/gocode/issues/46). Note that `nsf/gocode` is recommending people migrate off of `nsf/gocode` to `mdempsky/gocode`.
* **go-tools** (tools by dominikh such as staticcheck, megacheck, gosimple): sample tracking issue [dominikh/go-tools#328](https://github.com/dominikh/go-tools/issues/328).

In general, even if your editor, IDE or other tools have not yet been made module aware, much of their functionality should work with modules if you are using modules inside GOPATH and do `go mod vendor` (because then the proper dependencies should be picked up via GOPATH).

The full fix is to move programs that load packages off of `go/build` and onto `golang.org/x/tools/go/packages`, which understands how to locate packages in a module-aware manner. This will likely eventually become `go/packages`.

## FAQs — Additional Control

### What community tooling exists for working with modules?

The community is starting to build tooling on top of modules. For example:

* [github.com/rogpeppe/gohack](https://github.com/rogpeppe/gohack)
  * A new community tool to automate and greatly simplify `replace` and multi-module workflows, including allowing you to easily modify one of your dependencies 
  * For example, `gohack example.com/some/dependency` automatically clones the appropriate repository and adds the necessary `replace` directives to your `go.mod`
  * Remove all gohack replace statements with `gohack -u`
  * The project is continuing to expand to make other module-related workflows easier
* [github.com/marwan-at-work/mod](https://github.com/marwan-at-work/mod)
  * Command line tool to automatically upgrade/downgrade major versions for modules
  * Automatically adjusts `go.mod` files and related import statements in go source code
  * Helps with upgrades, or when first opting in to modules with a v2+ package
* [github.com/goware/modvendor](https://github.com/goware/modvendor)
  * Helps copy additional files into the `vendor/` folder, such as shell scripts, .cpp files, .proto files, etc.
  
### When should I use the replace directive?

* As described in the ['go.mod' concepts section above](https://github.com/golang/go/wiki/Modules#gomod), `replace` directives provide additional control in the top-level `go.mod` for what is actually used to satisfy a dependency found in the Go source or go.mod files, while `replace` directives in modules other than the main module are ignored when building the main module.
* The `replace` directive allows you to supply another import path that might be another module located in VCS (GitHub or elsewhere), or on your local filesystem with a relative or absolute file path. The new import path from the `replace` directive is used without needing to update the import paths in the actual source code.
* One sample use case is if you need to fix or investigate something in a dependency, you can have a local fork and add the something like the following in your top-level `go.mod`:
   * `replace example.com/original/import/path => /your/forked/import/path`
* `replace` also allows the top-level module control over the exact version used for a dependency, such as:
   * `replace example.com/some/dependency => example.com/some/dependency v1.2.3`
* `replace` also can be used to inform the go tooling of the relative or absolute on-disk location of modules in a multi-module project, such as:
   * `replace example.com/project/foo => ../foo`
* **Note**: in general, you can specify a version to the left of the `=>` in a replace directive, but typically it is less sensitive to change if you omit that (e.g., as done in the examples above).
* See the [tip documentation](https://tip.golang.org/cmd/go/#hdr-Edit_go_mod_from_tools_or_scripts) for more details.
* [github.com/rogpeppe/gohack](https://github.com/rogpeppe/gohack) makes these types of workflows much easier. See the [repository](https://github.com/rogpeppe/gohack) or the immediately prior FAQ for an overview.

### Can I work entirely outside of VCS on my local filesystem?

Yes. VCS is not required. 

This is very simple if you have a single module you want to edit at a time, and you can place the file tree containing the single `go.mod` in a convenient location.

If you want to have multiple inter-related modules on your local disk that you want to edit at the same time, then `replace` directives are one approach. Here is a sample `go.mod` that uses a `replace` with a relative path to point the `hello` module at the on-disk location of the `goodbye` module (without relying on any VCS):

```
module example.com/me/hello

require (
  example.com/me/goodbye v0.0.0
)

replace example.com/me/goodbye => ../goodbye
```
As shown in this example, if outside of VCS you can use `v0.0.0` as the version in the `require` directive. Note that the `require` directive is needed. (`replace foo => ../foo` doesn't yet work without a corresponding `require foo v0.0.0`: see [#26241](https://golang.org/issue/26241).)

A small runnable example is shown in this [thread](https://groups.google.com/d/msg/golang-nuts/1nYoAMFZVVM/eppaRW2rCAAJ).

### How do I use vendoring with modules? Is vendoring going away?

The initial series of `vgo` blog posts did propose dropping vendoring entirely, but [feedback](https://groups.google.com/d/msg/golang-dev/FTMScX1fsYk/uEUSjBAHAwAJ) from the community resulted in retaining support for vendoring.
 
In brief, to use vendoring with modules:
* `go mod vendor` resets the main module's vendor directory to include all packages needed to build and test all of the module's packages based on the state of the go.mod files and Go source code.
* By default, go commands like `go build` ignore the vendor directory when in module mode.
* The `-mod=vendor` flag (e.g., `go build -mod=vendor`) instructs the go commands to use the main module's top-level vendor directory to satisfy dependencies. The go commands in this mode therefore ignore the dependency descriptions in go.mod and assume that the vendor directory holds the correct copies of dependencies. Note that only the main module's top-level vendor directory is used; vendor directories in other locations are still ignored.
* Some people will want to routinely opt-in to vendoring by setting a `GOFLAGS=-mod=vendor` environment variable.

Older versions of Go such as 1.10 understand how to consume a vendor directory created by `go mod vendor`, so vendoring is one way to provide dependencies to older versions of Go that do not fully understand modules.

If you are considering using vendoring, it is worthwhile to read the ["Modules and vendoring"](https://tip.golang.org/cmd/go/#hdr-Modules_and_vendoring) and ["Make vendored copy of dependencies"](https://tip.golang.org/cmd/go/#hdr-Make_vendored_copy_of_dependencies) sections of the tip documentation.

### Are there "always on" module repositories and enterprise proxies?

Publicly hosted "always on" immutable module repositories and optional privately hosted proxies and repositories are becoming available.

For example:
* [Project Athens](https://github.com/gomods/athens): Open source project in the works and looking for contributors.
* [JFrog Artifactory](https://jfrog.com/artifactory/): Commercial offering. Support for Go 1.11 modules started with release 5.11 as described [here](https://jfrog.com/blog/goproxy-artifactory-go-registries/) and [here](https://www.jfrog.com/confluence/display/RTF/Go+Registry). From Artifactory version 6.2.0, please use [JFrog CLI 1.20.2](https://www.jfrog.com/confluence/display/CLI/CLI+for+JFrog+Artifactory#CLIforJFrogArtifactory-BuildingGoPackages) and above.

Note that you are not required to run a proxy. Rather, the go tooling in 1.11 has added optional proxy support via [GOPROXY](https://tip.golang.org/cmd/go/#hdr-Module_proxy_protocol) to enable more enterprise use cases (such as greater control), and also to better handle situations such as "GitHub is down" or people deleting GitHub repositories.

### Can I control when go.mod gets updated and when the go tools use the network to satisfy dependencies?

By default, a command like `go build` will reach out to the network as needed to satisfy imports.

Some teams will want to disallow the go tooling from touching the network at certain points, or will want greater control regarding when the go tooling updates `go.mod`, how dependencies are obtained, and how vendoring is used.

The go tooling provides a fair amount of flexibility to adjust or disable these default behaviors, including via `-mod=readonly`, `-mod=vendor`, `GOFLAGS`, `GOPROXY=off`, `GOPROXY=file:///filesystem/path`, `go mod vendor`, and `go mod download`.

The details on these options are spread throughout the official documentation. One community attempt at a consolidated overview of knobs related to these behaviors is [here](https://github.com/thepudds/go-module-knobs/blob/master/README.md), which includes links to the official documentation for more information.

### How do I use modules with CI systems such as Travis or CircleCI?

The simplest approach is likely just setting the environment variable `GO111MODULE=on`, which should work with most CI systems.

However, it can be valuable to run tests in CI on Go 1.11 with modules enabled as well as disabled, given some of your users will not have yet opted in to modules themselves. Vendoring is also a topic to consider.

The following two blog posts cover these topics more concretely:

* ["Using Go modules with vendor support on Travis CI"](https://arslan.io/2018/08/26/using-go-modules-with-vendor-support-on-travis-ci/) by Fatih Arslan 
* ["Go Modules and CircleCI"](https://medium.com/@toddkeech/go-modules-and-circleci-c0d6fac0b000) by Todd Keech 

## FAQs — go.mod and go.sum

### Why does 'go mod tidy' record indirect and test dependencies in my 'go.mod'?

The modules system records precise dependency requirements in your `go.mod`. (For more details, see the [go.mod concepts](https://github.com/golang/go/wiki/Modules#gomod) section above or the [go.mod tip documentation](https://tip.golang.org/cmd/go/#hdr-The_go_mod_file)).

`go mod tidy` updates your current `go.mod` to include the dependencies needed for tests in your module — if a test fails, we must know which dependencies were used in order to reproduce the failure.

`go mod tidy` also ensures your current `go.mod` reflects the dependency requirements for all possible combinations of OS, architecture, and build tags (as described [here](https://github.com/golang/go/issues/25971#issuecomment-399091682)). In contrast, other commands like `go build` and `go test` only update `go.mod` to provide the packages imported by the requested packages under the current `GOOS`, `GOARCH`, and build tags (which is one reason `go mod tidy` might add requirements that were not added by `go build` or similar).

If a dependency of your module does not itself have a `go.mod` (e.g., because the dependency has not yet opted in to modules itself), or if its `go.mod` file is missing one or more of its dependencies (e.g., because the module author did not run `go mod tidy`), then the missing transitive dependencies will be added to _your_ module's requirements, along with an `// indirect` comment to indicate that the dependency is not from a direct import within your module.  

Note that this also means that any missing test dependencies from your direct or indirect dependencies will also be recorded in your `go.mod`. (An example of when this is important: `go test all` runs the tests of _all_ direct and indirect dependencies of your module, which is one way to validate that your current combination of versions work together. If a test fails in one of your dependencies when you run `go test all`, it is important to have a complete set of test dependency information recorded so that you have reproducible `go test all` behavior).

In general, the behaviors described here are part of how modules provide 100% reproducible builds and tests by recording precise dependency information.

If you are curious as to why a particular module is showing up in your `go.mod`, you can run `go mod why -m <module>` to [answer](https://tip.golang.org/cmd/go/#hdr-Explain_why_packages_or_modules_are_needed) that question.  Other useful tools for inspecting requirements and versions include `go mod graph` and `go list -m all`.

### Is 'go.sum' a lock file? Why does 'go.sum' include information for module versions I am no longer using?

No, `go.sum` is not a lock file. For validation purposes, `go.sum` contains the expected cryptographic checksums of the content of specific module versions. See the [FAQ below](https://github.com/golang/go/wiki/Modules#should-i-commit-my-gosum-file-as-well-as-my-gomod-file) for more details on `go.sum` (including why you typically should check in `go.sum`) as well as the ["Module downloading and verification"](https://tip.golang.org/cmd/go/#hdr-Module_downloading_and_verification) section in the tip documentation.

In part because `go.sum` is not a lock file, it retains cryptographic checksums for module versions even after you stop using a module or particular module version. This allows validation of the checksums if you later resume using something, which provides additional safety.

In addition, your module's `go.sum` records checksums for all direct and indirect dependencies used in a build (and hence your `go.sum` will frequently have more modules listed than your `go.mod`).

### Should I still add a 'go.mod' file if I do not have any dependencies?

Yes. This supports working outside of GOPATH, helps communicate to the ecosystem that you are opting in to modules, and in addition the `module` directive in your `go.mod` serves as a definitive declaration of the identify of your code (which is one reason why import comments might eventually be deprecated). Of course, modules are purely an opt-in capability in Go 1.11.

### Should I commit my 'go.sum' file as well as my 'go.mod' file?

Typically your module's `go.sum` file should be committed along with your `go.mod` file. 

* `go.sum` contains the expected cryptographic checksums of the content of specific module versions.
* If someone clones your repository and downloads your dependencies using the go command, they will receive an error if there is any mismatch between their downloaded copies of your dependencies and the corresponding entries in your `go.sum`.
* In addition, `go mod verify` checks that the on-disk cached copies of module downloads still match the entries in `go.sum`.
* Note that `go.sum` is not a lock file as used in some alternative dependency management systems. (`go.mod` provides enough information for reproducible builds).
* See very brief [rationale here](https://twitter.com/FiloSottile/status/1029404663358087173) from Filippo Valsorda on why you should check in your `go.sum`. See the ["Module downloading and verification"](https://tip.golang.org/cmd/go/#hdr-Module_downloading_and_verification) section of the tip documentation for more details. See possible future extensions being discussed for example in [#24117](https://github.com/golang/go/issues/24117) and [#25530](https://github.com/golang/go/issues/25530).

## FAQs — Semantic Import Versioning

### Why must major version numbers appear in import paths?

Please see the discussion on the semantic import versioning and the import compatibility rule in the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) concepts section above. See also the [blog post announcing the proposal](https://blog.golang.org/versioning-proposal), which talks more about the motivation and justification for the import compatibility rule.

### Why are major versions v0, v1 omitted from import paths?"

Please see the question "Why are major versions v0, v1 omitted from import paths?" in the earlier [FAQ from the official proposal discussion](https://github.com/golang/go/issues/24301#issuecomment-371228664).

### What are some implications of tagging my project with major version v0, v1, or making breaking changes with v2+?

In response to a comment about *"k8s does minor releases but changes the Go API in each minor release"*, Russ Cox made the following [response](https://github.com/kubernetes/kubernetes/pull/65683#issuecomment-403705882) that highlights some implications for picking v0, v1, vs. frequently making breaking changes with v2, v3, v4, etc. with your project:

>  I don't fully understand the k8s dev cycle etc, but I think generally the k8s team needs to decide/confirm what they intend to guarantee to users about stability and then apply version numbers accordingly to express that.
> 
> * To make a promise about API compatibility (which seems like the best user experience!) then start doing that and use 1.X.Y.
> * To have the flexibility to make backwards-incompatible changes in every release but allow different parts of a large program to upgrade their code on different schedules, meaning different parts can use different major versions of the API in one program, then use X.Y.0, along with import paths like k8s.io/client/vX/foo.
> * To make no promises about API compatible and also require every build to have only one copy of the k8s libraries no matter what, with the implied forcing of all parts of a build to use the same version even if not all of them are ready for it, then use 0.X.Y.

On a related note, Kubernetes has some atypical build approaches (currently including custom wrapper scripts on top of godep), and hence Kubernetes is an imperfect example for many other projects, but it will likely be an interesting example as [Kubernetes moves towards adopting Go 1.11 modules](https://github.com/kubernetes/kubernetes/pull/64731#issuecomment-407345841). 

## FAQs — Minimal Version Selection

### Won't minimal version selection keep developers from getting important updates?

Please see the question "Won't minimal version selection keep developers from getting important updates?" in the earlier [FAQ from the official proposal discussion](https://github.com/golang/go/issues/24301#issuecomment-371228664).

## FAQs — Possible Problems

### Why does `go build` require gcc, and why are prebuilt packages such as net/http not used?

In short:

> Because the pre-built packages are non-module builds and can’t be reused. Sorry. Disable cgo for now or install gcc.

This is only an issue when opting in to modules (e.g., via `GO111MODULE=on`). See [#26988](https://github.com/golang/go/issues/26988#issuecomment-417886417) for additional discussion.

### Do modules work with relative imports like `import "./subdir"`?

No. See [#26645](https://github.com/golang/go/issues/26645#issuecomment-408572701), which includes:

> In modules, there finally is a name for the subdirectory. If the parent directory says "module m" then the subdirectory is imported as "m/subdir", no longer "./subdir".

### Some needed files may not be present in populated vendor directory

Only *.go files are copied inside vendor directory by `go mod vendor`, this is by design, see [#27618](https://github.com/golang/go/issues/27618).

## FAQs — Miscellaneous

### How did the `go mod` commands change in `go1.11beta3` and `go1.11` release?

In go1.11beta3 and go1.11, there was a significant change for the `go mod` commands. Older material and blogs might still use the older commands from before the change. See the [release documentation](https://golang.org/cmd/go/#hdr-Module_maintenance) and `go mod help` output for the up-to-date information:
```
$ go mod help
Go mod provides access to operations on modules.

Note that support for modules is built into all the go commands,
not just 'go mod'. For example, day-to-day adding, removing, upgrading,
and downgrading of dependencies should be done using 'go get'.
See 'go help modules' for an overview of module functionality.

Usage:

	go mod <command> [arguments]

The commands are:

	download    download modules to local cache
	edit        edit go.mod from tools or scripts
	graph       print module requirement graph
	init        initialize new module in current directory
	tidy        add missing and remove unused modules
	vendor      make vendored copy of dependencies
	verify      verify dependencies have expected content
	why         explain why packages or modules are needed

Use "go help mod <command>" for more information about a command.
```

For a historical reference, take a look at the [CL](https://go-review.googlesource.com/c/go/+/126655) briefly covering the rationale and the list of new vs. old commands (though further changed by 1.11 release):
```
Splitting out the individual commands makes both the docs
and the implementations dramatically easier to read.
It simplifies the command lines
(go mod -init -module m is now 'go mod init m')
and allows command-specific flags.
```


