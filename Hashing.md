Please consider move this into document for package ` hash `.

# Hashing

## The hash.Hash interface

All hashes defined in the standard library implement the hash.Hash interface. The Hash interface allows you to input data, get the sum (hash) of the previously inputted data, and forget previously inputted data. It also has some methods which return constants based on the hash type.

To input data, you use the Write method. For example:

```go
h.Write(byteSlice)
```

or

```go
io.Copy(h, file)
```

While Write returns an int and error, these are just to comply with the io.Writer interface. A hash will never return an error or an n != len(byteSlice).

At any time during data input, you can get the current sum by calling the Sum method. Use of the `Sum()` method will not effect future calls to sum. The most common way to use it is `sum := h.Sum(nil)`. What the `Sum()` method does is append the sum to the []byte parameter and return the new []byte. This can allow you to avoid allocating a new []byte each time you want the Sum. If you are summing often, you may do `md5sum := make([]byte, 16)` once and then do `h.Sum(md5sum[:0])` each time you want the new hash.

If you want to reuse an already created hash, you can use `Reset()` to ensure it forgets all previously inputted data.