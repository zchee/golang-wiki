# Fuzzing trophy case

This page collects issues that have been discovered using [Go's native fuzzing](https://github.com/golang/go/issues/44551).

## Contributing

If native fuzzing uncovered a bug in your project, please consider adding it to this list by editing this Wiki page directly, or by reaching out to katie@golang.org with the bug you'd like to share.

_Note: If you think the bug is a security issue, please report it responsibly to the respective team, and do not include it in this list until public disclosure._

## Trophies
<!-- If editing this list, please maintain alphabetical order -->

### Standard Library
* [go/scanner: inconsistent handling of NUL bytes in 1.17](https://github.com/golang/go/issues/46855)
* [time: ParseDuration can panic on invalid input](https://github.com/golang/go/issues/46883)

### Other projects
* [go-yaml/yaml/v3: yaml.Unmarshal() crashes on "#\n - - QI\xd7"](https://github.com/go-yaml/yaml/issues/744)
* [josephburnett/jd: crashes when validating JSON Patch test/replace operation](https://github.com/josephburnett/jd/commit/7064efc5df7c899ffc53b45be8915e3f4edc1684)
* [josephburnett/jd: JSON Patch to void failing round-trip](https://github.com/josephburnett/jd/commit/bd2fc2657f56c7c1f70a5971c18be32365afd1c7)
* [kokes/smda: nil pointer error](https://github.com/kokes/smda/commit/b41ac00b5f5acba60d93076347fc73fe2fbca340)
* [kokes/smda: out of bounds error](https://github.com/kokes/smda/commit/2c2548f211a1ed2c3547407e0b420e4340612278)
* [mvdan.cc/sh: syntax.Quote failed to quote the empty string](https://github.com/mvdan/sh/commit/92eab20da20af9c4005294abf937e387d87c8407)
* [mvdan.cc/sh: syntax.Quote misused `\x` escape sequences in mksh](https://github.com/mvdan/sh/commit/8bd780f971469bece51617a53da0e1c700c4a5b8)
* [mvdan.cc/sh: syntax.Quote can't quote the `0xFFFE` and `0xFFFF` runes in mksh](https://github.com/mvdan/sh/commit/6ff55fb976f3c39d1a382ff5af616c3665c7e501)
* [pelletier/go-toml: index out of range error in expect function](https://github.com/pelletier/go-toml/issues/561)
* [swaggest/form: panic on invalid keys in request](https://github.com/swaggest/form/issues/4)
* [yuin/goldmark: corner case errors](https://github.com/yuin/goldmark/issues/245)
* [DataDog/datadog-agent: fix edge case in tags normalization](https://github.com/DataDog/datadog-agent/pull/13235)


