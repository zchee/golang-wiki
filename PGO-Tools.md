---
title: PGO Tools
---

[Profile-guided optimization](https://go.dev/doc/pgo) (PGO) in the Go toolchain uses CPU pprof profiles as the PGO profile format. Though pprof is a widely-used format across many tools, Go's PGO imposes [specific requirements](https://go.dev/doc/pgo#alternative-sources) on the contents of profiles, which many tools across the ecosystem may not be compatible with.

This (non-exhaustive) page lists tools for collecting and working with profiles that are known to be compatible with PGO.

# Collecting profiles

* [`runtime/pprof`](https://pkg.go.dev/runtime/pprof), [`net/http/pprof`](https://pkg.go.dev/net/http/pprof): The Go standard library profiling functionality always provides PGO-compatible profiles.
* [Parca Agent](https://github.com/parca-dev/parca-agent) produces PGO-compatible profiles when paired with a symbolizer that produces metadata that includes function start lines, such as [Polar Signals Cloud](https://www.polarsignals.com/) or [Parca](https://www.parca.dev/) starting at version `v0.19.0`.

# Working with profiles

* `go tool pprof`/[standalone `pprof` CLI](https://github.com/google/pprof), [`github.com/google/pprof/profile`](https://pkg.go.dev/github.com/google/pprof/profile): The official `pprof` CLI and Go packages can perform various operations on profiles (filtering, merging multiple profiles, etc). These tools/packages generally leave metadata (e.g., symbolization, function start lines) intact across operations. Thus given a PGO-compatible input, they should produce a PGO-compatible output.
* [Parca](https://www.parca.dev/) and [Polar Signals Cloud](https://www.polarsignals.com/) provide various mechanisms to query and filter profiling data and download any query as a pprof file that will contain function start line metadata to be PGO-compatible.