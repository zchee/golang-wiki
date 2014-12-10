Since the introduction of the ` append ` built-in, most of the functionality of the ` container/vector ` package, which was removed in Go 1, can be replicated using ` append ` and ` copy `.

Here are the vector methods and their slice-manipulation analogues:

` AppendVector `
```
a = append(a, b...)
```
` Copy `
```
b = make([]T, len(a))
copy(b, a)
// or
b = append([]T(nil), a...)
```
` Cut `
```
a = append(a[:i], a[j:]...)
```
` Delete `
```
a = append(a[:i], a[i+1:]...)
// or
a = a[:i+copy(a[i:], a[i+1:])]
```
` Delete without preserving order `
```
a[i], a = a[len(a)-1], a[:len(a)-1]
```
**NOTE** If the type of the element is a _pointer_ or a struct with pointer fields, which need to be garbage collected, the above implementations of ` Cut ` and ` Delete ` have a potential _memory leak_ problem: some elements with values are still referenced by slice ` a ` and thus can not be collected. The following code can fix this problem:
> ` Cut `
```
copy(a[i:], a[j:])
for k, n := len(a)-j+i, len(a); k < n; k++ {
	a[k] = nil // or the zero value of T
} // for k
a = a[:len(a)-j+i]
```
> ` Delete `
```
copy(a[i:], a[i+1:])
a[len(a)-1] = nil // or the zero value of T
a = a[:len(a)-1]
```
> ` Delete without preserving order `
```
a[i], a[len(a)-1], a = a[len(a)-1], nil, a[:len(a)-1]
```

` Expand `
```
a = append(a[:i], append(make([]T, j), a[i:]...)...)
```
` Extend `
```
a = append(a, make([]T, j)...)
```

` Insert `
```
a = append(a[:i], append([]T{x}, a[i:]...)...)
```
**NOTE** The second ` append ` creates a new slice with its own underlying storage and  copies elements in ` a[i:] ` to that slice, and these elements are then copied back to slice ` a ` (by the first ` append `). The creation of the new slice (and thus memory garbage) and the second copy can be avoided by using an alternative way:
> ` Insert `
```
s = append(s, 0)
copy(s[i+1:], s[i:])
s[i] = x
```

` InsertVector `
```
a = append(a[:i], append(b, a[i:]...)...)
```
` Pop `
```
x, a = a[len(a)-1], a[:len(a)-1]
```
` Push `
```
a = append(a, x)
```

## Additional Tricks
### Filtering without allocating

This trick uses the fact that a slice shares the same backing array and capacity as the original, so the storage is reused for the filtered slice. Of course, the original contents are modified.

```
b := a[:0]
for _, x := range a {
	if f(x) {
		b = append(b, x)
	}
}
```