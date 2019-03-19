# Error Values: Frequently Asked Questions

The Go 2 [error values proposal](https://go.googlesource.com/proposal/+/master/design/29934-error-values.md) adds functionality to the [`errors`](https://tip.golang.org/pkg/errors) and [`fmt`](https://tip.golang.org/pkg/fmt) packages of the standard library for Go 1.13. There is also a compatibility package, [`golang.org/x/xerrors`](https://godoc.org/golang.org/x/xerrors), for earlier Go versions.

We suggest using the `xerrors` package for backwards compatibility. When you no longer wish to support Go versions before 1.13, use the corresponding standard library functions.

## How should I change my error-handling code to work with the new features?

You need to be prepared that errors you get may be wrapped. 

- If you currently compare errors using `==`, use `xerrors.Is` instead. Example:
   ```
   if err == io.ErrUnexpectedEOF
   ```
   becomes
   ```
   if xerrors.Is(err, io.ErrUnexpectedEOF)
   ```

   - Checks of the form `if err != nil` need not be changed.
   - Comparisons to `io.EOF` need not be changed, because `io.EOF` should never be wrapped.

- If you check for an error type using a type assertion or type switch, use `xerrors.As` instead. Example:
  ```
  if e, ok := err.(*os.PathError); ok
  ```
  becomes
  ```
  e := &os.PathError{}
  if xerrors.As(err, &e)
  ```
  - Also use this pattern to check whether an error implements an interface. (This is one of those rare cases when a pointer to an interface is appropriate.)
  - Rewrite a type switch as a sequence of if-elses.

## What formatting verb should I use to display errors?

It depends who you expect to see the error message, and why.

- If you are displaying an error so someone can diagnose a problem in your code, use `%+v` to display the maximum amount of detail. For example, an error that indicates a bug in your program should be displayed (or at least logged) with `%+v`.

- If the person who sees the error message is unlikely to know or care about modifying your program, you probably want to use `%v` (or, equivalently for errors, `%s`). For example, an error reading a file from a command-line program should probably be displayed with `%v`.

## I am already using `fmt.Errorf` with `%v` or `%s` to provide context for an error. When should I switch to `%w`?

It's common to see code like
```
if err := frob(thing); err != nil {
    return fmt.Errorf("while frobbing: %v", err)
}
```
With the new error features, that code continues to work as before; the only difference is that more information is captured and displayed.

Changing from `%v` to `%w` doesn't change how the error is displayed, but it does wrap `err`, the final argument to the `fmt.Errorf` call. Now the caller can access `err`, either by calling `Unwrap` on the returned error, or by using `errors.Is` or `errors.As` (which are merely convenience functions built on top of `Unwrap`).

So use `%w` if you want to expose the underlying error to your callers. Keep in mind that doing so may be exposing implementation detail that can constrain the evolution of your code. Callers can depend on the type and value of the error you're wrapping, so changing that error can now break them. For example, if your `accessDatabase` function uses Go's `database/sql` package, then it may encounter a `sql.ErrTxDone` error. If you return that error with `fmt.Errorf("accessing DB: %v", err)` then callers won't see that `sql.ErrTxtDone` is part of the error you return. But if you instead return `fmt.Errorf("accessing DB: %w", err)`, then a caller could reasonably write
```
err := accessDatabase(...)
if xerrors.Is(err, sql.ErrTxDone)
```
At that point, you must always return `sql.ErrTxDone` if you don't want to break your clients, even if you switch to a different database package.

## How can I add context to an error I'm already returning without breaking clients?

Say your code now looks like
```
return err
```
and you decide that you want to add more information to `err` before you return it. If you write
```
return fmt.Errorf("more info: %v", err)
```
then you might break your clients, because the identity of `err` is lost; only its message remains.

You could instead wrap the error by using `%w`, writing
```
return fmt.Errorf("more info: %w", err)
```
This will still break clients who use `==` or type assertion to test errors. But as we discussed in the first question of this FAQ, consumers of errors should migrate to the `Is` and `As` functions. If you can be sure that your clients have done so, then it is not a breaking change to switch from
```
return err
```
to
```
return fmt.Errorf("more info: %w", err)
```

## I'm writing new code, with no clients. Should I wrap returned errors or not?

Since you have no clients, you aren't constrained by backwards compatibility. But you still need to balance two opposing considerations:
- Giving client code access to underlying errors can help it make decisions, which can lead to better software.
- Every error you expose becomes part of your API: your clients may come to rely on it, so you can't change it.

For each error you return, you have to weigh the choice between helping your clients and locking yourself in. Of course, this choice is not unique to errors. In general, you have to decide if a feature of your code is important for clients to know, or an implementation detail. 

With errors, though, there is an intermediate choice: you can expose error details to people reading your code's error messages, without exposing the errors themselves to client code. You do that by using `fmt.Errorf` with `%s` or `%v` (as in the past), or by implementing the [`errors.Formatter`](https://tip.golang.org/pkg/errors/#Formatter) interface on a custom error type.

## I maintain a package that exports an error-checking predicate function. How should I adapt to the new features?

Your package has a function or method `IsX(error) bool` that reports whether an error has some property. Your situation is like that of the standard `os` package, which has several such functions. We recommend the approach we took there. The `os` package has several predicates, but we treated them all the same. For concreteness, we'll look at `os.IsExist`.

A natural thought would be to modify the predicate to unwrap the error it is passed, checking the property for each error in the chain of wrapped errors. We decided not to do this. A change in the behavior of `os.IsExist` for Go 1.13 would make it incompatible with earlier Go versions.

Instead, we made `errors.Is(err, os.ErrExist)` behave like `os.IsExist`, except that `Is` unwraps. (We did this by having some internal error types implement an `Is` method, as described in the documentation for [`errors.Is`](https://tip.golang.org/pkg/errors/#Is).) Using `errors.Is` will always work correctly, because it only will exist in Go versions 1.13 and higher. For older version of Go, you should recursively unwrap the error yourself, calling `os.IsExist` on each underlying error.

So we recommend:
- Don't change your `IsX(error) bool` function.
- If you don't already have one, add a global variable whose type implements `error` that represents the 
  condition that your function tests:
  ```
  var ErrX = errors.New("has property X")
  ```
- Add an `Is` method to the types for which `IsX` returns true. The `Is` method should return true if its argument 
  equals `ErrX`.