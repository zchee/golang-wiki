# Introduction

This is page tries to enumerate the Use Cases that call for generics and give a Go alternative without using generics.

Who knows, you might find you really didn't need generics for that at all!


# Details

**FIRST USE CASE: Generic Algorithm on data whose Type you Don't Yet Know**

...but needs to follow some Properties or Behaviours...

You just use interfaces to define the properties or behaviours your data needs to be able to be used by your Generic Algorithm. As exemplified by the sort package:

http://golang.org/pkg/sort/#Interface

# Unresolved USE CASES

- map() in Python: **map(lambda x:x\*2, range(100))**:
```
func Map(f interface{}, v interface{}) interface{} {
	// Reflection to solve f and v types
}
```
The reflect solution performance is really bad

- Polymorphic functions that operate on built-in generic types.
```
func KeyIntersection(a map[T1]T2, b map[T1]T2) map[T1]T2 {}
```

- Containers that must store non-interface values. (Various
motivations: control memory layout, require an immutable copy...)

# Under construction...

This page is under construction.

It feeds from a discussion thread on golang nuts:
http://groups.google.com/group/golang-nuts/browse_thread/thread/3d825ac84e742598