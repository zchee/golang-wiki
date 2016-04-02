# Go 1.1 "gotchas"

While Go 1.1 is compatible with Go 1.0, the [compatibility promise](http://golang.org/doc/go1compat.html) permits the Go authors to break existing programs if they were incorrect in the first place.

Here are a few ways in which the bug fixes in Go 1.1 may have broken your Go programs.


## Unknown foo.Bar field in struct literal

Struct field names must not include package qualifiers.
For example, take this struct with an embedded ` *bytes.Buffer ` field:

```
type S struct {
	*bytes.Buffer
}
```

In Go 1.0 the compiler would (incorrectly) accept this struct literal:

```
s := S{
	bytes.Buffer: new(bytes.Buffer),
}
```

Under Go 1.1 the compiler rejects this.
Instead you should use the field name without the package qualifier:

```
s := S{
	Buffer: new(bytes.Buffer),
}
```

## Initialization loop

The Go 1.1 compiler now better detects initialization loops.

For instance, the following code compiled under Go 1.0.

```
var funcVar = fn

func fn() {
	funcVar()
}
```

Such code must now use an ` init ` function for the variable assignment to avoid
the initialization loop.

```
var funcVar func()

func fn() {
	funcVar()
}

func init() {
	funcVar = fn
}
```

In particular, this affects users of App Engine's [delay package](https://developers.google.com/appengine/docs/go/taskqueue/delay).


## Cannot fallthrough final case in switch

Go 1.0 permitted fallthrough in the final case of a switch statement:

```
switch {
case false:
	fallthrough // fall through to 'true' case
case true:
	fallthrough // fall through to... nowhere?
}
```

A language change affecting [return requirements](http://golang.org/doc/go1.1#return) led us to make the superfluous fallthrough illegal.

The fix is to remove such statements from your code.


## Duplicate argument name in parameters and return values

A compiler bug permitted function type declarations with parameters and return values of the same name. This would compile under Go 1.0:

```
type T func(a int) (a int)
```

Under Go 1.1, the compiler gives an error:

```
	duplicate argument a
```

The fix is to rename the arguments so that they use different names.


## Package "go" forbidden

The import path "go" is now reserved. If you have a package in your workspace
whose import path is "go", you will need to rename it and move it somewhere
else.

While it was permitted, it is a bad idea to use this import path.
The standard library includes "go/parser", "go/ast", and so on.
It's posssible that a "go" package might be introduced in a future Go release,
making your "go" package unusable.

Please read [How to write Go code](http://golang.org/doc/code.html) for more
details about import paths.