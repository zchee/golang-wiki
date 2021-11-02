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
* [pelletier/go-toml: index out of range error in expect function](https://github.com/pelletier/go-toml/issues/561)
* [swaggest/form: panic on invalid keys in request](https://github.com/swaggest/form/issues/4)
* [yuin/goldmark: corner case errors](https://github.com/yuin/goldmark/issues/245)


