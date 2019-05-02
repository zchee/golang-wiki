Sometimes a package reaches the end of its development cycle and is considered complete. It continues to be maintained, meaning regressions or breakages are fixed, but the scope becomes frozen and no new features are meant to be accepted.

Freezing a package is a message primarily for developers and contributors to the package, not users. It does not imply that the package should not be used. For that, see the ["Deprecated" convention](Deprecated).

To signal that a package is frozen and is not accepting new features, add a paragraph to its doc comment stating that, and a recommendation on where to look for and where to contribute new features, if applicable.

## Examples

```
// The syslog package is frozen and is not accepting new features.
// Some external packages provide more functionality. See:
//
// 	https://godoc.org/?q=syslog
```

```
// The smtp package is frozen and is not accepting new features.
// Some external packages provide more functionality. See:
//
// 	https://godoc.org/?q=smtp
```

```
// The net/rpc package is frozen and is not accepting new features.
```

```
// The testing/quick package is frozen and is not accepting new features.
```

```
// The text/tabwriter package is frozen and is not accepting new features.
```

There are some examples [in the standard library](https://golang.org/search?q=frozen).