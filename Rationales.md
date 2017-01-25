# Introduction

This wiki entry will try to document the rationales behind some important language
decisions besides what's included in the Go FAQ and Effective Go.

# Language Features
### Why method receiver's base type cannot be pointer or interface?
Reference: https://groups.google.com/forum/#!topic/golang-nuts/aqTwXHaSC_Y

Go doesn't allow receiver's base type to be pointer to avoid possible ambiguity.
Suppose you have:
```
type T blah
type P *T

func (t *T) String() string { ... }
func (p P) String() string { ... }

var p P
```

Then the meaning of the expression ` (*p).String() ` is ambiguous, because it can refer to
both ` (*T).String ` and ` P.String `.

Go doesn't allow receiver's base type to be interfaces, because interfaces already have methods. (TODO)

### Select with closed channel

[Issue #11344](https://github.com/golang/go/issues/11344).

### Send to closed channel

[Issue #18511](https://github.com/golang/go/issues/18511).

# Memory Model

# Standard Library