# Well Known Struct Tags
## Background

Go offers [struct tags](https://golang.org/ref/spec#Tag) which are discoverable via reflection. These enjoy a wide range of use in the standard library in the JSON/XML and other encoding packages. The community welcomed them and build ORMs, further encodings, flag parsers and much more around them.

Since esp. while handling encodings and ORMs single sourcing data structures is beneficial for data structures.

## Problem description
Due to increased usage of Go and thus Go [struct tags](https://golang.org/ref/spec#Tag), clashes become inevitable. 

## Solution
The list below is a best effort to document well known struct tags used by packages which available to the public.

## Format of the list
* Struct tag as extracted by calling https://godoc.org/reflect#StructTag.Get with this tag as the `key` argument.
* Documentation link of this package using https://godoc.org

### Example entry
Tag | Documentation
----|-----
xml | https://godoc.org/encoding/xml

### Change Management
List entries can be added by anyone who creates a public package where a new tag is used.
List entries can be removed when the links to the package documentation stops working or the author(s) of that package requests it.

## List of Well Known Struct Tags
Tag    | Documentation
-------|-----
xml    | https://godoc.org/encoding/xml
json   | https://godoc.org/encoding/json
asn1   | https://godoc.org/encoding/asn1
reform | https://godoc.org/gopkg.in/reform.v1
