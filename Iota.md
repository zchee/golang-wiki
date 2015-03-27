# Summary

Go's ` iota ` identifier is used in ` const ` declarations to simplify definitions of incrementing numbers. Because it can be used in expressions, it provides a generality beyond that of simple enumerations.

The values of iota start at zero within each const block and increment by one each time it is seen.  This can be combined with the constant shorthand (leaving out everything after the constant name) to very concisely define related constants.

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