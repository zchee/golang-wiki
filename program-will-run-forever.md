```
package main

import (
	"time"
)

func init() {
	go func() {
		for {
			time.Sleep(time.Second)
		}
	}()
}
func main() {
	waitQueue := make(chan int)
	waitQueue <- 1
	return
}
```
go version 1.17.3
The program will never end and there will be no panic.
This is a bug.