# Compiler Optimizations

This page lists optimizations done by the compilers. Note that these are not guaranteed by the language specification.

## Zero-width types in interface values

Putting a zero-width type in an interface value doesn't allocate.

* **gc:** 1.0+
* **gccgo:** ?

## Word-sized value in an interface value

Putting a word-sized-or-less non-pointer type in an interface value doesn't allocate.

* **gc:** 1.0-1.3, but *not* in 1.4+
* **gccgo:** never

## Map lookup by []byte

For a map m of type map[string]T and []byte b, m[string(b)] doesn't allocate. (the temporary string copy of the byte slice isn't made)

* **gc:** 1.4+
* **gccgo:** ?

## Escape analysis: foo

TODO

## Escape analysis: bar

TODO
