# Error Values: Frequently Asked Questions

The Go 2 [error values proposal](https://go.googlesource.com/proposal/+/master/design/29934-error-values.md) adds functionality to the [`errors`](https://tip.golang.org/pkg/errors) and [`fmt`](https://tip.golang.org/pkg/fmt) packages of the standard library for Go 1.13. There is also a compatibility package, [`golang.org/x/xerrors`](https://godoc.org/golang.org/x/xerrors), for earlier Go versions.

We suggest using the `xerrors` package for backwards compatibility. When you no longer wish to support Go versions before 1.13, use the corresponding standard library functions.

## How should I change my error-handling code for Go 1.13?

You need to be prepared that errors you get may be wrapped. 

- If you currently compare errors using `==`, use `xerrors.Is` instead. Example:
   ```
   if err == io.ErrUnexpectedEOF
   ```
   becomes
   ```
   if xerrors.Is(err, io.ErrUnexpectedEOF)
   ```

   - Checks of the form `if err == nil` need not be changed.
   - Comparisons to `io.EOF` need not be changed, because `io.EOF` should never be wrapped.


