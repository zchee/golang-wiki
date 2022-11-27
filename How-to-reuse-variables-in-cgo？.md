I use GO code build a so file, and call it from go. at begin, i want to do some init job, so make sure the go call the shared library can reuse some variable. for example:
**main.go**
```
package main

import "C"
import (
	"fmt"
	"os"
	"os/signal"
	"syscall"
	"time"
)

var (
	globalConfig string
)

func main() {

}

//export search
func search() {
	fmt.Println(globalConfig)
}

//export start
func start() {
	// just keep running to keep globalConfig in RAM
	go forever()

	quitChannel := make(chan os.Signal, 1)
	signal.Notify(quitChannel, syscall.SIGINT, syscall.SIGTERM)
	<-quitChannel
}

func forever() {
	v := "global value"
	globalConfig = v
	for {
		time.Sleep(10 * time.Second)
		fmt.Println(globalConfig)
	}
}

```
and then generate the shared library.
```
go build -buildmode=c-shared -o libsdk.so main.go 
```
call the shared lib.  
**cgo1.go**
```
package main

/*
first step: export LD_LIBRARY_PATH="xxx sopath xxx"
*/

// #include "libsdk.h"
// #cgo LDFLAGS: -L. -lsdk
import "C"

func main() {
	C.start()
	// C.search()
}

```

**cgo2.go**
```
package main

/*
first step: export LD_LIBRARY_PATH="xxx sopath xxx"
*/

// #include "libsdk.h"
// #cgo LDFLAGS: -L. -lsdk
import "C"

func main() {
	// C.start()
	C.search()
}

```

and then the output first get the global value, the the second is null.

shouldn't shared lib share memory?