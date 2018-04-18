Here I used an unbuffered channel, but I received an unexpected result that it didn't hang on the channel 'c'.After one second, it printed timeout.
```
package main

import (
	"time"
	"fmt"
)

func do() error {
	var err error
	time.Sleep(time.Second * 10)
	fmt.Println("do something")
	return err
}

func main()  {
	c := make(chan error)
	go func() {do()}()
	select {
	case err := <-c:
		fmt.Println(err)
	case <-time.After(time.Second):
		fmt.Println("timeout")
		break
	}
}
```
