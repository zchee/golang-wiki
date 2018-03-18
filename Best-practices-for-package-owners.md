# Disclaimer: incomplete and unreviewed

This page is currently a draft and does not represent a final version of these recommendations. It might be incomplete or even wrong. It hasn't been reviewed or approved by anyone. Take it with a grain of salt.

## Best practices for package owners

Etiquette on how to properly build packages for the consumption of others can be hard to find. Implicit expectations exist, specially for open source libraries that can be used by anyone, often in ways unexpected by the package creator.

This page documents recommendations for package authors. These aren't universal truths but can be considered as a starting point.

* [Release tagging](#release-tagging)
* [Avoid breaking changes](#avoid-breaking-changes)
* [Meaningful errors](#meaningful-errors)
* [No logging](#no-logging)

### Release tagging

Creating releases with specific version numbers helps dependency management tools figure out upgrade paths for consumers of your library. [Semver](https://semver.org/) is the most widely used versioning style. It is useful specially to indicate major breaks in the package's API and is a major factor in [vgo](https://github.com/golang/vgo).

### Avoid breaking changes

Breaking changes force all consumers of a package to update their code. However, the number of users of a package tends to be far greater than the number of maintainers, even for small packages. Consider the time spent by all those users combined can be far greater than the time the maintainers would spend preventing the change. Only break your API with careful consideration and indicate it clearly with [release tagging](#release-tagging).

### Meaningful errors

In Go, [errors are values](https://blog.golang.org/errors-are-values). Errors indicate clearly situations that can be managed by the consumer of the library. If an operation can fail, return an error. Document on each function call what errors it can return and document what each error means and how to deal with it. This is essential for retrying operations, logging problems and overall stability of a program using your library.

### No logging

Each consumer of your library will do logging in a different way. Some will use the standard library logging, some will use logging libraries that extend the capabilities of stdlib logging. Logging can differ in many ways and should not be forced by the library. Provide [meaningful errors](#meaningful-errors) when logging looks like it could be useful and let the user decide what to do. When logging is absolutely necessary, make that clear on your package API using an interface to let the user pass his own logger into the library.