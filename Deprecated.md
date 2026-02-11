---
title: Deprecated
---

Sometimes an API feature such as a struct field, function, type, or even a whole package becomes
redundant or unnecessary.
When we want to discourage new programs from using it,
we mark that feature "deprecated".

In general, if an API still works and does not have significant downsides,
we do not formally mark it as deprecated, and instead
simply update the documentation to point to the preferred API.
When there is simply a newer, preferred API available, consider
adding a `//go:fix inline` annotation to gently steer consumers
toward the new API.
For changes in the Go standard library, consider proposing a modernizer.

To signal that an identifier should not be used, add a paragraph to its doc
comment that begins with `Deprecated:` followed by some information about the
deprecation, and a recommendation on what to use instead, if applicable.
The paragraph does not have to be the last paragraph in the doc comment.

[Some tools will warn on use of deprecated identifiers](https://staticcheck.io/docs/checks#SA1019)
and their docs [are hidden on pkg.go.dev](https://go.dev/issue/40850).

## Deprecations in the Go standard library

Marking an API feature deprecated can create work and
decisions for millions of Go developers using the feature.
Deprecating an API feature is an API change that must
be discussed using [the proposal process](https://go.dev/s/proposal).

In contrast to some other systems, an API feature being deprecated
_does not_ mean it is going to be removed in the future.
On the contrary, [Go 1 compatibility](https://go.dev/doc/go1compat)
means the feature will be preserved in its deprecated form
to keep existing programs running.

If function `F1` is being replaced by function `F2`
and the first release in which `F2` is available is Go 1.N,
then an official deprecation notice for `F1` should not be
added until Go 1.N+1.
This ensures that Go developers only see `F1` as deprecated
when all supported Go versions include `F2` and they can easily switch.

## Examples

```Go
type ResponseRecorder struct {
	// HeaderMap contains the headers explicitly set by the Handler.
	// It is an internal detail.
	//
	// Deprecated: HeaderMap exists for historical compatibility
	// and should not be used. To access the headers returned by a handler,
	// use the Response.Header map as returned by the Result method.
	HeaderMap http.Header
```

```Go
// Package rc4 implements the RC4 stream cipher.
//
// Deprecated: RC4 is cryptographically broken and should not be used
// except for compatibility with legacy systems.
//
// This package is frozen and no new functionality will be added.
package rc4
```

There are a few other examples [in the standard library](https://cs.opensource.google/search?q=Deprecated:%20language:go&ss=go%2Fgo).
