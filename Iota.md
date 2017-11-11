# Summary

Go's ` iota ` identifier is used in ` const ` declarations to simplify definitions of incrementing numbers. Because it can be used in expressions, it provides a generality beyond that of simple enumerations.

The values of iota is reset to 0 whenever the reserved word ` const ` appears in the source (i.e. each const block) and increments by one after each [ConstSpec](https://golang.org/ref/spec#ConstSpec) e.g. each Line.  This can be combined with the constant shorthand (leaving out everything after the constant name) to very concisely define related constants.

Iota: http://golang.org/doc/go_spec.html#Iota

Constant declarations: http://golang.org/doc/go_spec.html#Constant_declarations

# Examples

The official spec has two great examples:

http://golang.org/doc/go_spec.html#Iota

Here's one from Effective Go:

```
type ByteSize float64

const (
	_           = iota // ignore first value by assigning to blank identifier
	KB ByteSize = 1 << (10 * iota)
	MB
	GB
	TB
	PB
	EB
	ZB
	YB
)
```

Weekday enum example - How iota is calculated - From [Learn Go Programming Blog](https://blog.learngoprogramming.com):

![How iota works](https://cdn-images-1.medium.com/max/2000/1*sfAHT3zk-WjxSDRIDMpdaA.gif)

# Articles

* [Ultimate Visual Guide to Go Enums and Iota](https://blog.learngoprogramming.com/golang-const-type-enums-iota-bc4befd096d3) _2017-10-09_