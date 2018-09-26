This is just another way to deal with errors following Go2 draft structure.

If I understood correctly `handle` is used as defer in many proposals, which, could be a drawback in case we want the function to fail as soon as error occurs.
So, a better scenario could be as follows:

1) Unhandled error occurs - it is thrown and parent function should handle it
2) Handled error occurs - `handle` function catches it and performs some operations before exiting the function (in the handle function one can decide to throw an error again if he/she needs to add additional info to the err)

``` Golang
func CopyFile(src, dst string) throws error {
	r := os.Open(src) // option 1
	defer r.Close()

	w := os.Create(dst)
	err := io.Copy(w, r) // option 2
	err2 := w.Close() // option 2
	handle err || err2 { // handle function is executed if `err` or `err2` is not equal to `nil`
		w.Close()
		os.Remove(dst)
		// optionally throw error here
		// return errors.New("could not copy.")
	}
}
```
Actually I am not sure why `try catch` is not considered, it seems it could be the best solution (familiar syntax)

``` Golang
func CopyFile(src, dst string) throws error {
	r := os.Open(src) // thrown so parent function can catch it or pass to its parent
	defer r.Close()

	w := os.Create(dst)
	try { // handle special case
		io.Copy(w, r)
		w.Close()
	} catch err {
		w.Close()
		os.Remove(dst)
		// optionally throw error here
		// return errors.New("could not copy.")
		// or to make it consistent with other languages throw it
		// throw errors.New("could not copy.")
	}
}
```
***

Methods without comments:

1. 
``` Golang
func CopyFile(src, dst string) throws error {
	r := os.Open(src)
	defer r.Close()

	w := os.Create(dst)
	err := io.Copy(w, r)
	err2 := w.Close()
	handle err || err2 {
		w.Close()
		os.Remove(dst)
	}
}
```
2. 

``` Golang
func CopyFile(src, dst string) throws error {
	r := os.Open(src)
	defer r.Close()

	w := os.Create(dst)
	try {
		io.Copy(w, r)
		w.Close()
	} catch err {
		w.Close()
		os.Remove(dst)
	}
}
```