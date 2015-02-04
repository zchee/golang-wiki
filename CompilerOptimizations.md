# Compiler Optimizations

This page lists optimizations done by the compilers. Note that these are not guaranteed by the language specification.

## Interface values

### Zero-width types in interface values

Putting a zero-width type in an interface value doesn't allocate.

* **gc:** 1.0+
* **gccgo:** ?

### Word-sized value in an interface value

Putting a word-sized-or-less non-pointer type in an interface value doesn't allocate.

* **gc:** 1.0-1.3, but *not* in 1.4+
* **gccgo:** never

## string and []byte

### Map lookup by []byte

For a map m of type map[string]T and []byte b, m[string(b)] doesn't allocate. (the temporary string copy of the byte slice isn't made)

* **gc:** 1.4+
* **gccgo:** ?

## Escape analysis

TODO

## Idioms

### Optimized memclr

For a slice or array s, loops of the form

```go
for i := range s {
	a[i] = <zero value for element of s>
}
```

are converted into efficient runtime memclr calls. [Issue](golang.org/issue/5373) and [commit](https://golang.org/change/f03c9202c43e0abb130669852082117ca50aa9b1).

* **gc:** 1.5+
* **gccgo:** ?
