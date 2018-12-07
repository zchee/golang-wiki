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
  * [What are some general things I can spot check if I am seeing a problem?](https://github.com/golang/go/wiki/Modules#what-are-some-general-things-i-can-spot-check-if-i-am-seeing-a-problem)
  * [What can I check if I not seeing the expected version of a dependency?](https://github.com/golang/go/wiki/Modules#what-can-i-check-if-i-am-not-seeing-the-expected-version-of-a-dependency)
  * [Why am I getting an error 'cannot find module providing package foo'?](https://github.com/golang/go/wiki/Modules#why-am-i-getting-an-error-cannot-find-module-providing-package-foo)
  * [Why does 'go mod init' give the error 'cannot determine module path for source directory'?](https://github.com/golang/go/wiki/Modules#why-does-go-mod-init-give-the-error-cannot-determine-module-path-for-source-directory)
  * [Why does 'go build' require gcc, and why are prebuilt packages such as net/http not used?](https://github.com/golang/go/wiki/Modules#why-does-go-build-require-gcc-and-why-are-prebuilt-packages-such-as-nethttp-not-used)
  * [Do modules work with relative imports like `import "./subdir"`?](https://github.com/golang/go/wiki/Modules#do-modules-work-with-relative-imports-like-import-subdir)
  * [Some needed files may not be present in populated vendor directory](https://github.com/golang/go/wiki/Modules#some-needed-files-may-not-be-present-in-populated-vendor-directory)

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

Modules must be semantically versioned according to [semver](https://semver.org/) in the form `v(major).(minor).(patch)`, such as  `v0.1.0` or `v1.2.3`. The leading `v` is required. If using Git, [tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging) released commits with their versions. Public and private module repositories and proxies are becoming available (see for example FAQ [below](https://github.com/golang/go/wiki/Modules#are-there-always-on-module-repositories-and-enterprise-proxies)).

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

All of the packages in a module share a common prefix – the *module path*. The `go.mod` file defines the module path via the `module` directive. For example, if you are defining a module for two packages `example.com/my/project/foo` and `example.com/my/project/bar`, the first line in your `go.mod` file typically would be `module example.com/my/project`, and the corresponding on-disk structure could be:

```
project/
├── go.mod
├── bar
│   └── bar.go
└── foo
    └── foo.go
```

`exclude` and `replace` directives only operate on the current (“main”) module. `exclude` and `replace` directives in modules other than the main module are ignored when building the main module. The `replace` and `exclude` statements therefore allow the main module complete control over its own build, without also being subject to complete control by dependencies.  (See FAQ [below](https://github.com/golang/go/wiki/Modules#when-should-i-use-the-replace-directive) for discussion of when to use a `replace` directive).

In Go source code, packages are imported using the full path including the module. For example:
```
import "example.com/my/module/v2/pkg/foo"
```
This imports package `foo` from the v2 version of module `example.com/my/module`.

### Version Selection

If you add a new import to your source code that is not yet covered by a `require` in `go.mod`, most go commands like 'go build' and 'go test' will automatically look up the proper module and add the *highest* version of that new direct dependency to your module's `go.mod` as a `require` directive. For example, if your new import corresponds to dependency M whose latest tagged release version is `v1.2.3`, your module's `go.mod` will end up with `require M v1.2.3`, which indicates module M is a dependency with allowed version >= v1.2.3 (and < v2, given v2 is considered incompatible with v1).

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

Recall [semver](https://semver.org/) requires a major version change when a v1 or higher package makes a backwards incompatible change. The result of following both the import compatibility rule and semver is called _Semantic Import Versioning_, where the major version is included in the import path — this ensures the import path changes any time the major version increments due to a break in compatibility.

As a result of Semantic Import Versioning, code opting in to Go modules **must comply with these rules**: 
* Follow [semver](https://semver.org/) (with tags such as `v1.2.3`).
* If the module is version v2 or higher, the major version of the module _must_ be included in both the module path in the `go.mod` file (e.g., `module example.com/my/mod/v2`) and the package import path (e.g., `import "example.com/my/mod/v2/mypkg"`).
* If the module is version v0 or v1, do _not_ include the major version in either the module path or the import path.

In general, packages with different import paths are different packages. For example, `math/rand` is a different package than `crypto/rand`. This is also true if different import paths are due to different major versions appearing in the import path. Thus `example.com/my/mod/mypkg` is a different package than `example.com/my/mod/v2/mypkg`, and both may be imported in a single build, which among other benefits helps with diamond dependency problems and also allows a v1 module to be implemented in terms of its v2 replacement or vice versa.

See the ["Module compatibility and semantic versioning"](https://golang.org/cmd/go/#hdr-Module_compatibility_and_semantic_versioning) section of the `go` command documentation for more details on Semantic Import Versioning, and see https://semver.org for more about semantic versioning.

This section so far has been focused on code that has opted in to modules and imports other modules. However, putting major versions in import paths for v2+ modules could create incompatibilities with older versions of Go, or with code that has not yet opted in to modules. To help with this, there are three important transitional special cases or exceptions to the behavior and rules described above. These transitional exceptions will become less important over time as more packages opt in to modules. 

**Three Transitional Exceptions**

1. **gopkg.in**

    Existing code that uses import paths starting with `gopkg.in` (such as `gopkg.in/yaml.v1` and `gopkg.in/yaml.v2`) can continue to use those forms for their module paths and import paths even after opting in to modules.

2. **'+incompatible' when importing non-module v2+ packages**

    A module can import a v2+ package that has not opted in to modules itself. A non-module v2+ package that has a valid v2+ [semver](semver.org) tag will be recorded with an `+incompatible` suffix in the importing module's `go.mod` file. The `+incompatible` suffix indicates that even though the v2+ package has a valid v2+ [semver](semver.org) tag such as `v2.0.0`, the v2+ package has not actively opted in to modules and hence that v2+ package is assumed to have _not_ been created with an understanding of the implications of Semantic Import Versioning and how to use major versions in import paths. Therefore, when operating in [module mode](https://github.com/golang/go/wiki/Modules#when-do-i-get-old-behavior-vs-new-module-based-behavior), the `go` tool will treat a non-module v2+ package as an (incompatible) extension of the v1 version series of the package and assume the package has no awareness of Semantic Import Versioning, and the `+incompatible` suffix is an indication that the `go` tool is doing so. 

3. **"Minimal module compatibility" when module mode is not enabled**
    
    To help with backwards compatibility, Go versions 1.9.7+, 1.10.3+ and 1.11 have been updated to make it easier for code built with those releases to be able to properly consume v2+ modules _without_ requiring modification of pre-existing code. This behavior is called "minimal module compatibility", and it only takes effect when full [module mode](https://github.com/golang/go/wiki/Modules#when-do-i-get-old-behavior-vs-new-module-based-behavior) is disabled for the `go` tool, such as if such as you have set `GO111MODULE=off` in Go 1.11, or are using Go versions 1.9.7+ or 1.10.3+. When relying on this "minimal module compatibility" mechanism in Go 1.9.7+, 1.10.3+ and 1.11, a package that has _not_ opted in to modules would _not_ include the major version in the import path for any imported v2+ modules. In contrast, a package that _has_ opted in to modules _must_ include the major version in the import path to import any v2+ modules (in order to properly import the v2+ module when the `go` tool is operating in full module mode with full awareness of Semantic Import Versioning).

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

   Note that if your dependencies include v2+ modules, or if you are initializing a v2+ module, then after running `go mod init` you might also need to edit your `go.mod` and `.go` code to add `/vN` to import paths and module paths as described in the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above. This applies even if `go mod init` automatically converted your dependency information from `dep` or other dependency managers. (Because of this, after running `go mod init`, you typically should not run `go mod tidy` until you have successfully run `go build ./...` or similar, which is the sequence shown in this section).

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

For more information on all of these topics, the primary entry point to the official modules documentation is [available on golang.org](https://golang.org/cmd/go/#hdr-Modules__module_versions__and_more).

## How to Upgrade and Downgrade Dependencies

Day-to-day adding, removing, upgrading, and downgrading of dependencies should be done using 'go get', which will automatically update the `go.mod` file.

In addition, go commands like 'go build', 'go test', or even 'go list' will automatically add new dependencies as needed to satisfy imports (updating `go.mod` and downloading the new dependencies).

To upgrade to the latest version for all transitive dependencies of the current module:
 * run `go get -u` to use the latest *minor or patch* releases
 * run `go get -u=patch` to use the latest *patch* releases

To upgrade or downgrade to a more specific version, 'go get' allows version selection to be overridden by adding an @version suffix or "module query" to the package argument, such as `go get github.com/gorilla/mux@v1.6.2`, `go get foo@e3702bed2`, or `go get foo@'<v1.6.2'`. 

`go get foo` updates to the latest version with a [semver](https://semver.org/) tag. (This is  equivalent to `go get foo@latest` — in other words, `@latest` is the default if no `@` version is specified).

Using a branch name such as `go get foo@master` is one way to obtain the latest commit regardless of whether or not it has a semver tag.

In general, module queries that do not resolve to a semver tag will be recorded as [pseudo-versions](https://tip.golang.org/cmd/go/#hdr-Pseudo_versions) in the `go.mod` file.

Modules are capable of consuming packages that have not yet opted into modules, including recording any available semver tags in `go.mod` and using those semver tags to upgrade or downgrade. Modules can also consume packages that do not yet have any proper semver tags (in which case they will be recorded using pseudo-versions in `go.mod`).

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

Your new module release becomes available to consumers once you push the new release tags.

### Releasing Modules (v2 or Higher)

If you are releasing a v2 or higher module, please first review the discussion in the ["Semantic Import Versioning" ](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above, which includes why major versions are included in the module path and import path for v2+ modules, as well as how Go versions 1.9.7+ and 1.10.3+ have been updated to simplify that transition.

Note that if you adopting modules for the first time for a pre-existing repository or set of packages that have already been tagged `v2.0.0` or higher before adopting modules, then the [recommended best practice](https://github.com/golang/go/issues/25967#issuecomment-422828770) is to increment the major version when first adopting modules. For example, if you are the author of `foo`, and the latest tag for the `foo` repository is `v2.2.2`, and `foo` has not yet adopted modules, then the best practice would be to use `v3.0.0` for the first release of `foo` to adopt modules (and hence the first release of `foo` to contain a `go.mod` file). Incrementing the major version in this case provides greater clarity to consumers of `foo`, allows for additional non-module patches or minor releases on the v2 series of `foo` if needed, and provides a strong signal for a module-based consumer of `foo` that different major versions result if you do `import "foo"` and a corresponding `require foo v2.2.2+incompatible`, vs. `import "foo/v3"` and a corresponding `require foo/v3 v3.0.0`. (Note that this advice regarding incrementing the major version when first adopting modules does _not_ apply to pre-existing repos or packages whose latest versions are v0.x.x or v1.x.x).

There are two alternative mechanisms to release a v2 or higher module. Note that with both techniques, the new module release becomes available to consumers when the module author pushes the new tags. Using the example of creating a `v3.0.0` release, the two options are:

1. **Major branch**: Update the `go.mod` file to include a `/v3` at the end of the module path in the `module` directive (e.g., `module github.com/my/module/v3`). Update import statements within the module to also use `/v3` (e.g., `import "github.com/my/module/v3/mypkg"`). Tag the release with `v3.0.0`. 
   * Go versions 1.9.7+, 1.10.3+, and 1.11 are able to properly consume and build a v2+ module created using this approach without requiring updates to consumer code that has not yet opted in to modules (as described in the the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above). 
   * A community tool [github.com/marwan-at-work/mod](https://github.com/marwan-at-work/mod) helps automate this procedure. See the [repository](https://github.com/marwan-at-work/mod) or the [community tooling FAQ](https://github.com/golang/go/wiki/Modules#what-community-tooling-exists-for-working-with-modules) below for an overview.
   * To avoid confusion with this approach, consider putting the `v3.*.*` commits for the module on a separate v3 branch.
   * **Note:** creating a new branch is _not_ required. If instead you have been previously releasing on master and would prefer to tag `v3.0.0` on master, that is a viable option. (If you do decide to tag `v3.0.0` on master, you can consider creating a v2 branch for any future v2 bug fixes).

2. **Major subdirectory**: Create a new `v3` subdirectory (e.g., `my/module/v3`) and place a new `go.mod` file in that subdirectory. The module path must end with `/v3`. Copy or move the code into the `v3` subdirectory. Update import statements within the module to also use `/v3` (e.g., `import "github.com/my/module/v3/mypkg"`). Tag the release with `v3.0.0`.
   * This provides greater backwards compatibility. In particular, Go versions older than 1.9.7 and 1.10.3 are also able to properly consume and build a v2+ module created using this approach.
   * A more sophisticated approach here could exploit type aliases (introduced in Go 1.9) and forwarding shims between major versions residing in different subdirectories.  This can provide additional compatibility and allow one major version to be implemented in terms of another major version, but would entail more work for a module author. An in-progress tool to automate this is `goforward`. Please see [here](https://golang.org/cl/137076) for more details and rationale, along with a functioning initial version of `goforward`.

See https://research.swtch.com/vgo-module for a more in-depth discussion of these alternatives.

## Migration Considerations

This section attempts to briefly enumerate the major decisions to be made when migrating to modules as well as list other migration-related topics. References are generally provided to other sections for more details.

This material is primarily based on best practices that have emerged from the community as part of the modules experiment; this is therefore a work-in-progress section that will improve over time as the community gains more experience.

Summary:

* The modules system is designed to allow different packages in the overall Go ecosystem to opt in at different rates.
* Packages that are already on version v2 or higher have additional migration considerations, primarily due to the implications of [Semantic Import versioning](https://github.com/golang/go/wiki/Modules#semantic-import-versioning). 
  * New packages and packages on v0 or v1 have substantially fewer considerations when adopting modules.
* Modules defined with Go 1.11 can be used by older Go versions (although the exact Go versions depends on the strategy used by the main module and its dependencies, as outlined below).

Migration topics:

#### Automatic Migration from Prior Dependency Managers

  * `go mod init` automatically translates the required information from [dep, glide, govendor, godep and 5 other pre-existing dependency managers](https://tip.golang.org/pkg/cmd/go/internal/modconv/?m=all#pkg-variables) into a `go.mod `file that produces the equivalent build.
  * If you are creating a v2+ module, be sure your `module` directive in the converted `go.mod` includes the appropriate `/vN` (e.g., `module foo/v3`).
  * Note that if you are importing v2+ modules, you might need to do some manual adjustments after an initial conversion in order to add `/vN` to the `require` statements that `go mod init` generates after translating from a prior dependency manager. See the ["How to Define a Module"](https://github.com/golang/go/wiki/Modules#how-to-define-a-module) section above for more details.
  * In addition, `go mod init` will not edit your `.go` code to add any required `/vN` to import statements. See the ["Semantic Import versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) and ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) sections above for the required steps, including some options around community tools to automate the conversion.

#### Providing Dependency Information to Older Versions of Go

  * Older versions of Go understand how to consume a vendor directory created by `go mod vendor`. Therefore, vendoring is one way for a module to provide dependencies to older versions of Go that do not fully understand modules. See the [vendoring FAQ](https://github.com/golang/go/wiki/Modules#how-do-i-use-vendoring-with-modules-is-vendoring-going-away) and the `go` command [documentation](https://tip.golang.org/cmd/go/#hdr-Modules_and_vendoring) for more details.

#### Incrementing the Major Version When First Adopting Modules with v2+ Packages

* If you have packages that have already been tagged v2.0.0 or higher before adopting modules, then the recommended best practice is to increment the major version when first adopting modules. For example, if you are on `v2.0.1` and have not yet adopted modules, then you would use `v3.0.0` for the first release that adopts modules. See the ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) section above for more details.

#### v2+ Modules Allow Multiple Major Versions Within a Single Build

* If a module is on v2 or higher, an implication is that multiple major versions can be in a single build (e.g., `foo` and `foo/v3` might end up in a single build).
  * This flows naturally from the rule that "packages with different import paths are different packages".
  * When this happens, there will be there multiple copies of package-level state (e.g., package-level state for `foo` and package-level state for `foo/v3`) as well as each major version will run its own `init` function.
  * This approach helps with multiple aspects of the modules system, including helping with diamond dependency problems, gradual migration to new versions within large code bases, and allowing a major version to be implemented as a shim around a different major version.
* See the "Avoiding Singleton Problems" section of https://research.swtch.com/vgo-import or [#27514](https://github.com/golang/go/issues/27514) for some related discussion.

#### Modules Consuming Non-Module Code

  * Modules are capable of consuming packages that have not yet opted into modules, with the appropriate package version information recorded in the importing module's `go.mod`.  Modules can consume packages that do not yet have any proper semver tags. See FAQ [below](https://github.com/golang/go/wiki/Modules#can-a-module-consume-a-package-that-has-not-opted-in-to-modules) for more details.
  * Modules can also import a v2+ package that has not opted into modules. It will be recorded with an `+incompatible` suffix if the imported v2+ package has valid semver tags. See FAQ [below](https://github.com/golang/go/wiki/Modules#can-a-module-consume-a-v2-package-that-has-not-opted-into-modules-what-does-incompatible-mean) for more details.
  
#### Non-Module Code Consuming Modules

  * **Non-module code consuming v0 and v1 modules**:  
     * Code that has not yet opted in to modules can consume and build v0 and v1 modules (without any requirement related to the Go version used).

  * **Non-module code consuming v2+ modules**:
  
    * Go versions 1.9.7+, 1.10.3+ and 1.11 have been updated so that code built with those releases can properly consume v2+ modules without requiring modification of pre-existing code as described in the ["Semantic Import versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) and ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) sections above.

    * Go versions prior to 1.9.7 and 1.10.3 can consume v2+ modules if the v2+ module was created following the "Major subdirectory" approach outlined in the ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) section.

#### Strategies for Authors of Pre-Existing v2+ Packages

There are currently three top-level strategies for a pre-existing v2+ package considering opting in to modules. Each of these top-level strategies then has follow-on decisions and variations (as touched on above).

1. **Require clients to use Go versions 1.9.7+, 1.10.3+, or 1.11+**. 

    The approach uses the "Major Branch" approach and relies on the "minimal module awareness" that was backported to 1.9.7 and 1.10.3. See the ["Semantic Import versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) and ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) sections above for more details.

2. **Allow clients to use even older Go versions like Go 1.8**. 

    This approach uses the "Major Subdirectory" approach and involves creating a subdirectory such as `/v2` or `/v3`. See the ["Semantic Import versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) and ["Releasing Modules (v2 or Higher)"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) sections above for more details.

3. **Wait on opting in to modules**.  

    In this strategy, things continue to work with client code that has opted in to modules as well as with client code that has not opted in to modules. As time goes by, Go versions 1.9.7+, 1.10.3+, and 1.11+ will be out for an increasingly longer time period, and at some point in the future, it becomes more natural or client-friendly to require Go versions 1.9.7+/1.10.3+/1.11+, and at that point in time, you can implement strategy 1 above (requiring Go versions 1.9.7+, 1.10.3+, or 1.11+) or even strategy 2 above (though if you are ultimately going to go with strategy 2 above in order to support older Go versions like 1.8, then that is something you can do now).

#### Updating Pre-Existing Install Instructions

  * Pre-modules, it is common for install instructions to include `go get -u foo`. If you are publishing a module `foo`, consider dropping the `-u` for modules-based consumers.
     * `-u` asks the `go` tool to upgrade all the direct and indirect dependencies of `foo`. 
	 * A module consumer might choose to run `go get -u foo` later, but there are more benefits of ["High Fidelity Builds"](https://github.com/golang/proposal/blob/master/design/24301-versioned-go.md#update-timing--high-fidelity-builds) if `-u` is not part of the initial install instructions. See ["How to Upgrade and Downgrade Dependencies"](https://github.com/golang/go/wiki/Modules#how-to-upgrade-and-downgrade-dependencies) for more details.
     * `go get -u foo` does still work, and can still be a valid choice for install instructions.
  * In addition, `go get foo` is not strictly needed for a module-based consumer. 
     * Simply adding an import statement `import "foo"` is sufficient. (Later commands like `go build` or `go test` will automatically download `foo` and update `go.mod` as needed).
  * Module-based consumers will not use a `vendor` directory by default. 
     * Module-based consumer do not strictly need to use `vendor` when consuming a module given the information contained in `go.mod`, but some pre-existing install instructions assume the `go` tool will use `vendor` by default. See the [vendoring FAQ](https://github.com/golang/go/wiki/Modules#how-do-i-use-vendoring-with-modules-is-vendoring-going-away) for more details.
  * Install instructions that include `go get foo/...` might have issues in some cases (see discussion in [#27215](https://github.com/golang/go/issues/27215#issuecomment-427672781)).
  
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

## FAQs

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

4. `gobin` is a module-aware command to install and run main packages. By default, `gobin` installs/runs main packages without first needing to manually create a module, but with the `-m` flag it can be told to use an existing module to resolve dependencies. Please see the `gobin` [README](https://github.com/myitcv/gobin#usage) and [FAQ](https://github.com/myitcv/gobin/wiki/FAQ) for details and additional use cases.

5. Create a `go.mod` you use to track your globally installed tools, such as in `~/global-tools/go.mod`, and `cd` to that directory prior to running `go get` or `go install` for any globally installed tools. 

6. Create a `go.mod` for each tool in separate directories, such as `~/tools/gorename/go.mod` and `~/tools/goimports/go.mod`, and `cd` to that appropriate directory prior to running `go get` or `go install` for the tool. 

This current limitation will be resolved. However, the primary issue is that modules are currently opt-in, and a full solution will likely wait until GO111MODULE=on becomes the default behavior. See [#24250](https://github.com/golang/go/issues/24250#issuecomment-377553022) for more discussion, including this comment:

> This clearly must work eventually. The thing I'm not sure about is exactly what this does as far as the version is concerned: does it create a temporary module root and go.mod, do the install, and then throw it away? Probably. But I'm not completely sure, and for now I didn't want to confuse people by making vgo do things outside go.mod trees. Certainly the eventual go command integration has to support this.

This FAQ has been discussing tracking _globally_ installed tools.
 
If instead you want to track the tools required by a _specific_ module, see the next FAQ.

### How can I track tool dependencies for a module?

If you:
 *  want to use a go-based tool (e.g. `stringer`) while working on a module, and
 *  want to ensure that everyone is using the same version of that tool while tracking the tool's version in your module's `go.mod` file

then one currently recommended approach is to add a `tools.go` file to your module that includes import statements for the tools of interest (such as `import _ "golang.org/x/tools/cmd/stringer"`), along with a `// +build tools` build constraint. The import statements allow the `go` command to precisely record the version information for your tools in your module's `go.mod`, while the `// +build tools` build constraint prevents your normal builds from actually importing your tools.

For a concrete example of how to do this, please see this ["Go Modules by Example" walkthrough](https://github.com/go-modules-by-example/index/blob/master/010_tools/README.md).

A discussion of the approach along with an earlier concrete example of how to do this is in [this comment in #25922](https://github.com/golang/go/issues/25922#issuecomment-412992431).

The brief rationale (also from [#25922](https://github.com/golang/go/issues/25922#issuecomment-402918061)):

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
  * Remove all gohack replace statements with `gohack undo`
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
* In general, you have the option of specifying a version to the left of the `=>` in a replace directive, but typically it is less sensitive to change if you omit that (e.g., as done in all of the `replace` examples above).
* **Note**: a `require` directive is needed even when doing a `replace`. For example, you cannot do `replace foo => ../foo` without a corresponding `require` for `foo`. (If you are not sure what version to use in the `require` directive, you can often use `v0.0.0` such as `require foo v0.0.0`; see [#26241](https://golang.org/issue/26241)).
* You can confirm you are getting your expected versions by running `go list -m all`, which shows you the actual final versions that will be used in your build including taking into account `replace` statements.
* See the ['go mod edit' documentation](https://golang.org/cmd/go/#hdr-Edit_go_mod_from_tools_or_scripts) for more details.
* [github.com/rogpeppe/gohack](https://github.com/rogpeppe/gohack) makes these types of workflows much easier, especially if your goal is to have mutable checkouts of dependencies of a module.  See the [repository](https://github.com/rogpeppe/gohack) or the immediately prior FAQ for an overview.
* See the next FAQ for the details of using `replace` to work entirely outside of VCS.

### Can I work entirely outside of VCS on my local filesystem?

Yes. VCS is not required. 

This is very simple if you have a single module you want to edit at a time outside of VCS (and you either have only one module in total, or if the other modules reside in VCS). In this case, you can place the file tree containing the single `go.mod` in a convenient location. Your `go build`, `go test` and similar commands will work even if your single module is outside of VCS (without requiring any use of `replace` in your `go.mod`).

If you want to have multiple inter-related modules on your local disk that you want to edit at the same time, then `replace` directives are one approach. Here is a sample `go.mod` that uses a `replace` with a relative path to point the `hello` module at the on-disk location of the `goodbye` module (without relying on any VCS):

```
module example.com/me/hello

require (
  example.com/me/goodbye v0.0.0
)

replace example.com/me/goodbye => ../goodbye
```
As shown in this example, if outside of VCS you can use `v0.0.0` as the version in the `require` directive. Note that as mentioned in the prior FAQ, the `require` directive is needed here. (`replace example.com/me/goodbye => ../goodbye` does not yet work without a corresponding `require example.com/me/goodbye v0.0.0`; this might change in the future with [#26241](https://golang.org/issue/26241)).

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

Another reason you might have `// indirect` dependencies in your `go.mod` file is if you have upgraded (or downgraded) one of your indirect dependencies beyond what is required by your direct dependencies, such as if you ran `go get -u` or `go get foo@1.2.3`. The go tooling needs a place to record those new versions, and it does so in your `go.mod` file (and it does not reach down into your dependencies to modify _their_ `go.mod` files).

In general, the behaviors described above are part of how modules provide 100% reproducible builds and tests by recording precise dependency information.

If you are curious as to why a particular module is showing up in your `go.mod`, you can run `go mod why -m <module>` to [answer](https://tip.golang.org/cmd/go/#hdr-Explain_why_packages_or_modules_are_needed) that question.  Other useful tools for inspecting requirements and versions include `go mod graph` and `go list -m all`.

### Is 'go.sum' a lock file? Why does 'go.sum' include information for module versions I am no longer using?

No, `go.sum` is not a lock file. The `go.mod` files in a build provide enough information for 100% reproducible builds.

For validation purposes, `go.sum` contains the expected cryptographic checksums of the content of specific module versions. See the [FAQ below](https://github.com/golang/go/wiki/Modules#should-i-commit-my-gosum-file-as-well-as-my-gomod-file) for more details on `go.sum` (including why you typically should check in `go.sum`) as well as the ["Module downloading and verification"](https://tip.golang.org/cmd/go/#hdr-Module_downloading_and_verification) section in the tip documentation.

In part because `go.sum` is not a lock file, it retains cryptographic checksums for module versions even after you stop using a module or particular module version. This allows validation of the checksums if you later resume using something, which provides additional safety.

In addition, your module's `go.sum` records checksums for all direct and indirect dependencies used in a build (and hence your `go.sum` will frequently have more modules listed than your `go.mod`).

### Should I commit my 'go.sum' file as well as my 'go.mod' file?

Typically your module's `go.sum` file should be committed along with your `go.mod` file. 

* `go.sum` contains the expected cryptographic checksums of the content of specific module versions.
* If someone clones your repository and downloads your dependencies using the go command, they will receive an error if there is any mismatch between their downloaded copies of your dependencies and the corresponding entries in your `go.sum`.
* In addition, `go mod verify` checks that the on-disk cached copies of module downloads still match the entries in `go.sum`.
* Note that `go.sum` is not a lock file as used in some alternative dependency management systems. (`go.mod` provides enough information for reproducible builds).
* See very brief [rationale here](https://twitter.com/FiloSottile/status/1029404663358087173) from Filippo Valsorda on why you should check in your `go.sum`. See the ["Module downloading and verification"](https://tip.golang.org/cmd/go/#hdr-Module_downloading_and_verification) section of the tip documentation for more details. See possible future extensions being discussed for example in [#24117](https://github.com/golang/go/issues/24117) and [#25530](https://github.com/golang/go/issues/25530).

### Should I still add a 'go.mod' file if I do not have any dependencies?

Yes. This supports working outside of GOPATH, helps communicate to the ecosystem that you are opting in to modules, and in addition the `module` directive in your `go.mod` serves as a definitive declaration of the identify of your code (which is one reason why import comments might eventually be deprecated). Of course, modules are purely an opt-in capability in Go 1.11.

## FAQs — Semantic Import Versioning

### Why must major version numbers appear in import paths?

Please see the discussion on the Semantic Import Versioning and the import compatibility rule in the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) concepts section above. See also the [blog post announcing the proposal](https://blog.golang.org/versioning-proposal), which talks more about the motivation and justification for the import compatibility rule.

### Why are major versions v0, v1 omitted from import paths?"

Please see the question "Why are major versions v0, v1 omitted from import paths?" in the earlier [FAQ from the official proposal discussion](https://github.com/golang/go/issues/24301#issuecomment-371228664).

### Can a module consume a package that has not opted in to modules?

Yes.

If a repository has not opted in to modules but has been tagged with valid [semver](https://semver.org) tags (including the required leading `v`), then those semver tags can be used in a `go get`, and a corresponding semver version will be record in the importing module's `go.mod` file. If the repository does not have any valid semver tags, then the repository's version will be recorded with a ["pseudo-version"](https://golang.org/cmd/go/#hdr-Pseudo_versions) such as ` v0.0.0-20171006230638-a6e239ea1c69` (which includes a timestamp and a commit hash, and which are designed to allow a total ordering across versions recored in `go.mod` and to make it easier to reason about which recorded versions are "later" than another recorded version).

For example, if the latest version of package `foo` is tagged `v1.2.3` but `foo` has not itself opted in to modules, then running `go get foo` or `go get foo@v1.2.3` from inside module M will be recorded in module M's `go.mod` file as:

```
require  foo  v1.2.3
```

The `go` tool will also use available semver tags for a non-module package in additional workflows (such as `go list -u=patch`, which upgrades the dependencies of a module to available patch releases, or `go list -u -m all`, which shows available upgrades, etc.).

Please see the next FAQs for additional details related to v2+ packages that have not opted in to modules.

### Can a module consume a v2+ package that has not opted into modules? What does '+incompatible' mean?
 
Yes, a module can import a v2+ package that has not opted into modules, and if the imported v2+ package has a valid [semver](semver.org) tag, it will be recorded with an `+incompatible` suffix.

**Additional Details**

Please be familiar with the material in the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above.

It is helpful to first review some core principles that are generally useful but particularly important to keep in mind when thinking about the behavior described in this FAQ.

The following core principles are _always_ true when the `go` tool is operating in module mode (e.g., `GO111MODULE=on`):

1. A package's import path defines the identify of the package.
   * Packages with _different_ import paths are treated as _different_ packages.
   * Packages with the _same_ import path are treated as the _same_ package (and this is true _even if_ the VCS tags say the packages have different major versions).
2. An import path without a `/vN` is treated as a v1 or v0 module (and this is true _even if_ the imported package has not opted in to modules and has VCS tags that say the major version is greater than 1).
3. The module path (such as `module foo/v2`) declared at the start of a module's `go.mod` file is both:
   * the definitive declaration of that module's identity
   * the definitive declaration of how that module must be imported by consuming code

As we will see in the next FAQ, these principles are not always true when the `go` tool is _not_ in module mode, but these principles are always true when the `go` tool _is_ in module mode.

In short, the `+incompatible` suffix indicates that principle 2 above is in effect when the following are true:
* an imported package has not opted in to modules, and
* its VCS tags say the major version is greater than 1, and
* principle 2 is overriding the VCS tags – the import path without a `/vN` is treated as a v1 or v0 module (even though the VCS tags say otherwise)

When the `go` tool is in module mode, it will assume a non-module v2+ package has no awareness of Semantic Import Versioning and treat it as an (incompatible) extension of the v1 version series of the package (and the `+incompatible suffix` is an indication that the `go` tool is doing so).

**Example**

For example, suppose:
* `oldpackage` is a package that predates the introduction of modules
* `oldpackage` has never opted in to modules (and hence does not have a `go.mod` itself)
* `oldpackage` has a valid semver tag `v3.0.1`, which is its latest tag

In this case, running for example `go get oldpackage@latest` from inside module M will record the following in module M's `go.mod` file:

```
require  oldpackage  v3.0.1+incompatible
```

Note that there is no `/v3` used at the end of `oldpackage` in the `go get` command above or in the recorded `require` directive – using `/vN` in module paths and import paths is a feature of [Semantic Import Versioning](https://github.com/golang/go/wiki/Modules#semantic-import-versioning), and `oldpackage` has not signaled its acceptance and understanding of Semantic Import Versioning given `oldpackage` has not opted into modules by having a `go.mod` file within `oldpackage` itself. In other words, even though `oldpackage` has a [semver](https://semver.org) tag of `v3.0.1`, `oldpackage` is not granted the rights and responsibilities of [Semantic Import Versioning](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) (such as using `/vN` in import paths) because `oldpackage` has not yet stated its desire to do so.

The `+incompatible` suffix indicates that the `v3.0.1` version of `oldpackage` has not actively opted in to modules, and hence the `v3.0.1` version of `oldpackage` is assumed to _not_ understand Semantic Import Versioning or how to use major versions in import paths. Therefore, when operating in [module mode](https://github.com/golang/go/wiki/Modules#when-do-i-get-old-behavior-vs-new-module-based-behavior), the `go` tool will treat the non-module `v3.0.1` version of `oldpackage` as an (incompatible) extension of the v1 version series of `oldpackage` and assume that the `v3.0.1` version of `oldpackage` has no awareness of Semantic Import Versioning, and the `+incompatible` suffix is an indication that the `go` tool is doing so. 

The fact that the the `v3.0.1` version of `oldpackage` is considered to be part of the v1 release series according to Semantic Import Versioning means for example that versions `v1.0.0`, `v2.0.0`, and `v3.0.1` are all always imported using the same import path:

```
import  "oldpackage"
```

Note again that there is no `/v3` used at the end of `oldpackage`.

In general, packages with different import paths are different packages. In this example, given versions `v1.0.0`, `v2.0.0`, and `v3.0.1` of `oldpackage` would all be imported using the same import path, they are therefore treated by a build as the same package (again because `oldpackage` has not yet opted in to Semantic Import Versioning), with a single copy of `oldpackage` ending up in any given build. (The version used will be the semantically highest of the versions listed in any `require` directives; see ["Version Selection"](https://github.com/golang/go/wiki/Modules#version-selection)).

If we suppose that later a new `v4.0.0` release of `oldpackage` is created that adopts modules and hence contains a `go.mod` file, that is the signal that `oldpackage` now understands the rights and responsibilities of Semantic Import Versioning, and hence a module-based consumer would now import using `/v4` in the import path:

```
import  "oldpackage/v4"
```

and the version would be recorded as:

```
require  oldpackage/v4  v4.0.0
```

`oldpackage/v4` is now a different import path than `oldpackage`, and hence a different package.  Two copies (one for each import path) would end up in a module-aware build if some consumers in the build have `import "oldpackage/v4"` while other consumers in the same build have `import "oldpackage"`. This is desirable as part of the strategy to allow gradual adoption of modules. In addition, even after modules are out of their current transitional phase, this behavior is also desirable to allow gradual code evolution over time with different consumers upgrading at different rates to newer versions (e.g., allowing different consumers in a large build to choose to upgrade at different rates from `oldpackage/v4` to some future `oldpackage/v5`).

### How are v2+ modules treated in a build if modules support is not enabled? How does "minimal module compatibility" work in 1.9.7+, 1.10.3+, and 1.11?

When considering older Go versions or Go code that has not yet opted in to modules, Semantic Import Versioning has significant backwards compatibility implications related to v2+ modules.

As described in the ["Semantic Import Versioning"](https://github.com/golang/go/wiki/Modules#semantic-import-versioning) section above:
* a module that is version v2 or higher must include a `/vN` in its own module path declared in its `go.mod`.  
* a module-based consumer (that is, code that has opted in to modules) must include a `/vN` in the import path to import a v2+ module. 

However, the ecosystem is expected to proceed at varying paces of adoption for modules and Semantic Import Versioning.

As described in more detail in the ["How to Release a v2+ Module"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) section, in the "Major Subdirectory" approach, the author of a v2+ module creates subdirectories such as `mymodule/v2` or `mymodule/v3` and moves or copies the approriate packages underneath those subdirectories. This means the traditional import path logic (even in older Go releases such as Go 1.8 or 1.7) will find the appropriate packages upon seeing an import statement such as `import "mymodule/v2/mypkg"`. Hence, packages residing in a "Major Subdirectory" v2+ module will be found and used even if modules support is not enabled (whether that is because you are running Go 1.11 and have not enabled modules, or because you are running a older version like Go 1.7, 1.8, 1.9 or 1.10 that does not have full module support).  Please see the ["How to Release a v2+ Module"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) section for more details on the "Major Subdirectory" approach.

The remainder of this FAQ is focused on the "Major Branch" approach described in the ["How to Release a v2+ Module"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) section. In the "Major Branch" approach, no `/vN` subdirectories are created and instead the module version information is communicated by the `go.mod` file and by applying semver tags to commits (which often will be on `master`, but could be on different branches).

In order to help during the current transitional period, "minimal module compatibility" was [introduced](https://go-review.googlesource.com/c/go/+/109340) to Go 1.11 to provide greater compatibility for Go code that has not yet opted in to modules, and that "minimal module compatibility" was also backported to Go 1.9.7 and 1.10.3 (where those versions are effectively always operating with full module mode disabled given those older Go versions do not have full module support).

"Minimal module compatibility" provides backwards compatibility for v2+ modules in GOPATH mode without relying on the module author creating `/vN` subdirectories (and hence "minimal module compatibility" provides an alternative to the ["Major Subdirectory"](https://github.com/golang/go/wiki/Modules#releasing-modules-v2-or-higher) approach to backwards compatibility).

The primary goals of "minimal module compatibility" are:

1. Allow older Go versions 1.9.7+ and 1.10.3+ to be able to more easily compile modules that are using Semantic Import Versioning with `/vN` in import paths, and provide that same behavior when [module mode](https://github.com/golang/go/wiki/Modules#when-do-i-get-old-behavior-vs-new-module-based-behavior) is disabled in Go 1.11.

2. Allow old code to be able to consume a v2+ module without requiring that old consumer code to immediately change to using a new `/vN` import path when consuming a v2+ module.  

**Additional Details – "Minimal Module Compatibility"**

"Minimal module compatibility" only takes effect when full [module mode](https://github.com/golang/go/wiki/Modules#when-do-i-get-old-behavior-vs-new-module-based-behavior) is disabled for the `go` tool, such as if you have set `GO111MODULE=off` in Go 1.11, or are using Go versions 1.9.7+ or 1.10.3+.

When a v2+ module author has _not_ created `/v2` or `/vN` subdirectories and you are instead relying on the "minimal module compatibility" mechanism in Go 1.9.7+, 1.10.3+ and 1.11:

* A package that has _not_ opted in to modules would _not_ include the major version in the import path for any imported v2+ modules. 
* In contrast, a package that _has_ opted in to modules _must_ include the major version in the import path to import any v2+ modules (in order to properly import a v2+ module when the `go` tool is operating in full module mode). 
  * If a package has opted in to modules, but does not include the major version in the import path when importing a v2+ modules, it will not import a v2+ version of that module when the `go` tool is operating in full module mode. (A package that has opted in to modules is assumed to "speak" Semantic Import Versioning. If `foo` is a module with v2+ versions, then under Semantic Import Versioning saying `import "foo"` means import the v1 Semantic Import Versioning series of `foo`). 
* The mechanism used to implement "minimal module compatibility" is intentionally very narrow:
  * The entirety of the logic is – when operating in GOPATH mode, an unresolvable import statement containing a `/vN` will be tried again after removing the `/vN` if the import statement is inside code that has opted in to modules (that is, import statements in `.go` files within a tree with a valid `go.mod` file). 
  * The net effect is that an import statement such as `import "foo/v2"` within code that lives inside of a module will still compile correctly in GOPATH mode in 1.9.7+, 1.10.3+ and 1.11, and it will resolve as if it said `import "foo"` (without the `/v2`), which means it will use the version of `foo` that resides in your GOPATH without being confused by the extra `/v2`.
  * It does not affect anything else, including it does not the affect paths used in the `go` command line (such as arguments to `go get` or `go list`).
* Note there is therefore more than one valid import path for a v2+ module used in GOPATH mode under "minimal module compatibility", all of which resolve to the pre-modules import path (that is, the import path without a `/vN`).
  * When running in full modules mode, there are no exceptions to the rule "packages with different import paths are different packages" (including vendoring has been refined to also adhere to this rule in full modules mode).
  * For example, when operating in GOPATH mode, `import "foo/v2"` in module-based code resolves to the same code residing in your GOPATH as `import "foo"`, and the build ends up with one copy of `foo` – in particular, whatever version is on disk in GOPATH. This behavior is for backwards compatibility, and this allows module-based code with  `import "foo/v2"` to compile even in GOPATH mode in 1.9.7+, 1.10.3+ and 1.11.
 * In contrast, when the `go` tool is operating in full module mode, different import paths always resolve to different packages (for example, if `foo` is a v2+ module, then `import "foo"` is asking for a v1 version of `foo` vs. `import "foo/v2"` is asking for a v2 version of `foo`).

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

### What are some general things I can spot check if I am seeing a problem?

* Double-check that modules are enabled by running `go env` to confirm it does not show an empty value for the read-only `GOMOD` variable.
   * Note: you never set `GOMOD` as a variable because it is effectively read-only debug output that `go env` outputs.  
* If you are setting `GO111MODULE=on` to enable modules, double-check that it is not accidentally the plural `GO111MODULES=on`. (People sometimes naturally include the `S` because the feature is often called "modules").
* If vendoring is expected to be used, double-check check that the `-mod=vendor` flag is being passed to `go build `or similar, or that `GOFLAGS=-mod=vendor` is set. 
   * Modules by default ignore the `vendor` directory unless you ask the `go` tool to use `vendor`.
* It is frequently helpful to check `go list -m all` to see the list of actual versions selected for your build
  * `go list -m all` usually gives you more detail compared to if you were to instead just look a `go.mod` file. 
* If running `go get foo` fails in some way, you should check the output from `go get -v foo` or `go get -v -x foo` 
* You can check to see if you are using a particularly old git version
  * Older versions of git were a common source of problems for the `vgo` prototype and Go 1.11 beta, but much less frequently in the GA 1.11. 
* If you are using Docker, it can be helpful to check if you can reproduce the behavior outside of Docker (and if the behavior only occurs in Docker, the list of bullets above can be used as a starting point to compare results between inside Docker vs. outside).

### What can I check if I am not seeing the expected version of a dependency?

1. A good first step is to run `go mod tidy`. There is some chance this might resolve the issue, but it will also help put your `go.mod` file into a consistent state with respect to your `.go` source code, which will help make any subsequent investigation easier.

2. The second step usually should be to check `go list -m all` to see the list of actual versions selected for your build.  `go list -m all` shows you the final selected versions, including for indirect dependencies and after resolving versions for any shared dependencies. It also shows the outcome of any `replace` and `exclude` directives.

3. A good next step can be to examine the output of `go mod graph` or `go mod graph | grep <module-of-interest>`.  `go mod graph` prints the module requirement graph (including taking into account replacements). Each line in the output has two fields: the first column is a consuming module, and the second column is one of that module's requirements (including the version required by that consuming module).  This can be a quick way to see which modules are requiring a particular dependency, including when your build has different version numbers required for shared dependencies.

`go mod why -m <module>` can also be useful here, although it is typically more useful for seeing why a dependency is included at all (rather than why a dependency ends up with a particular version).

`go list` provides many more variations of queries that can be useful to interrogate your modules if needed.

A more detailed set of commands and examples can be seen in a runnable "Go Modules by Example" [walkthough](https://github.com/go-modules-by-example/index/tree/master/018_go_list_mod_graph_why).

### Why am I getting an error 'cannot find module providing package foo'?

This is a general error message that can occur for several different underlying causes.

In some cases, this error is simply due to a mistyped path, so the first step likely should be to double-check for incorrect paths based on the details listed in the error message.

If you have not already done so, a good next step is often to try `go get -v foo`:

* In general, `go get` will often provide more a detailed error message than `go build`.
* The `-v` flag for `go get` prints more details, though be mindful that certain "errors" such as 404 errors _might_ be expected based on how a remote repository was configured.
* If the nature of the problem is still not clear, you can also try the more verbose `go get -v -x foo`, which also shows the git or other VCS commands being issued.  (If warranted, you can often execute the same git commands outside of the context of the `go` tool for troubleshooting purposes).

Some other possible causes:

* You might see the error `cannot find module providing package foo` if you have issued `go build` or `go build .` but do not have any `.go` source files in the current directory. If this is what you are encountering, the solution might be an alternative invocation such as `go build ./...` (where the `...` expands out to subdirecories within the current module). See [#27122](https://github.com/golang/go/issues/27122).

* The module cache in Go 1.11 can cause this error, including in the face of network issues or multiple `go` commands executing in parallel (see [#26794](https://github.com/golang/go/issues/26794), which is addressed for Go 1.12).  You can copy $GOPATH/pkg/mod to a backup directory (in case further investigation is warranted later), run `go clean -modcache`, and then see whether the original problem persists.

### Why does 'go mod init' give the error 'cannot determine module path for source directory'?

`go mod init` without any arguments will attempt to guess the proper module path based on different hints such as VCS meta data. However, it is not expected that `go mod init` will always be able to guess the proper module path.

If `go mod init` gives you this error, those heuristics were not able to guess, and you must supply the module path yourself (such as `go mod init github.com/you/hello`).

### Why does 'go build' require gcc, and why are prebuilt packages such as net/http not used?

In short:

> Because the pre-built packages are non-module builds and can’t be reused. Sorry. Disable cgo for now or install gcc.

This is only an issue when opting in to modules (e.g., via `GO111MODULE=on`). See [#26988](https://github.com/golang/go/issues/26988#issuecomment-417886417) for additional discussion.

### Do modules work with relative imports like `import "./subdir"`?

No. See [#26645](https://github.com/golang/go/issues/26645#issuecomment-408572701), which includes:

> In modules, there finally is a name for the subdirectory. If the parent directory says "module m" then the subdirectory is imported as "m/subdir", no longer "./subdir".

### Some needed files may not be present in populated vendor directory

Directories without `.go` files are not copied inside the `vendor` directory by `go mod vendor`. This is by design. 

In short, setting aside any particular vendoring behavior – the overall model for go builds is that the files needed to build a package should be in the directory with the `.go` files.

Using the example of cgo – modifying C source code in other directories will not trigger a rebuild, and instead your build will use stale cache entries. The cgo documentation now [includes](https://go-review.googlesource.com/c/go/+/125297/5/src/cmd/cgo/doc.go):

> Note that changes to files in other directories do not cause the package
to be recompiled, so _all non-Go source code for the package should be
stored in the package directory_, not in subdirectories.

A community tool https://github.com/goware/modvendor allows you to easily copy a complete set of .c, .h, .s, .proto or other files from a module into the `vendor` director. Although this can be helpful, some care must be taken to make sure your go build is being handled properly in general (regardless of vendoring) if you have files needed to build a package that are outside of the directory with the `.go` files.

See additional discussion in [#26366](https://github.com/golang/go/issues/26366#issuecomment-405683150).
