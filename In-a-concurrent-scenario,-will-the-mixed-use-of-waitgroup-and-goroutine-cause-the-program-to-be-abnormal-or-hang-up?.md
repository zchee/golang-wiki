### What did you do?
``` go
type waitGroup struct {
	sync.WaitGroup
}

func (w *waitGroup) Wrap(fn func()) {
	w.Add(1)
	go func() {
		fn()
		w.Done()
	}()
}

func (w *waitGroup) WrapRecover(fn func()) {
	w.Add(1)
	go func() {
		defer func() {
			if err := recover(); err != nil {
				log.Println("exec recover: ", err)
			}
		}()

		fn()
		w.Done()
	}()
}

func getData(i int64) string {
	return strconv.FormatInt(i, 10)
}

func demo(ctx context.Context) error {
	go func() {
		ticker := time.NewTicker(500 * time.Millisecond)
		defer ticker.Stop()
		var i int64
		var wg = &waitGroup{}
		for {
			select {
			case <-ticker.C:
				data := getData(i)
				i++
				wg.Wrap(func() {
					log.Println("data: ", data)
				})
			case <-ctx.Done():
				wg.Wait()
				return
			}
		}
	}()

	return nil
}
```

## main.go
``` go
package main

import (
	"context"
	"fmt"
	"log"
	"net/http"
	"net/http/pprof"
	"os"
	"os/signal"
	"strconv"
	"sync"
	"syscall"
	"time"
)

var (
	port = 1339
	wait = 3 * time.Second
)

func init() {
	httpMux := http.NewServeMux()
	httpMux.HandleFunc("/debug/pprof/", pprof.Index)
	httpMux.HandleFunc("/debug/pprof/cmdline", pprof.Cmdline)
	httpMux.HandleFunc("/debug/pprof/profile", pprof.Profile)
	httpMux.HandleFunc("/debug/pprof/symbol", pprof.Symbol)
	httpMux.HandleFunc("/debug/pprof/trace", pprof.Trace)
	httpMux.HandleFunc("/check", func(w http.ResponseWriter, r *http.Request) {
		w.Write([]byte(`{"alive": true}`))
	})

	go func() {
		defer func() {
			if err := recover(); err != nil {
				log.Println("PProf exec recover: ", err)
			}
		}()

		log.Println("server PProf run on: ", port)

		if err := http.ListenAndServe(fmt.Sprintf("0.0.0.0:%d", port), httpMux); err != nil {
			log.Println("PProf listen error: ", err)
		}

	}()

}

func main() {
	ctx1, cancelFn := context.WithCancel(context.Background())
	demo(ctx1)

	// graceful exit
	ch := make(chan os.Signal, 1)
	// We'll accept graceful shutdowns when quit via SIGINT (Ctrl+C)
	// recv signal to exit main goroutine
	// window signal
	signal.Notify(ch, syscall.SIGINT, syscall.SIGTERM, os.Interrupt, syscall.SIGHUP)

	// linux signal if you use linux on production,please use this code.
	// signal.Notify(ch, syscall.SIGINT, syscall.SIGTERM, syscall.SIGUSR2, os.Interrupt, syscall.SIGHUP)

	// Block until we receive our signal.
	sig := <-ch

	cancelFn()

	log.Println("exit signal: ", sig.String())
	// Create a deadline to wait for.
	ctx, cancel := context.WithTimeout(context.Background(), wait)
	defer cancel()

	<-ctx.Done()

	log.Println("services shutting down")
}

type waitGroup struct {
	sync.WaitGroup
}

func (w *waitGroup) Wrap(fn func()) {
	w.Add(1)
	go func() {
		fn()
		w.Done()
	}()
}

func (w *waitGroup) WrapRecover(fn func()) {
	w.Add(1)
	go func() {
		defer func() {
			if err := recover(); err != nil {
				log.Println("exec recover: ", err)
			}
		}()

		fn()
		w.Done()
	}()
}

func getData(i int64) string {
	return strconv.FormatInt(i, 10)
}

func demo(ctx context.Context) error {
	go func() {
		ticker := time.NewTicker(500 * time.Millisecond)
		defer ticker.Stop()

		var i int64
		var wg = &waitGroup{}
		for {
			select {
			case <-ticker.C:
				data := getData(i)
				i++
				wg.Wrap(func() {
					log.Println("data: ", data)
				})
			case <-ctx.Done():
				wg.Wait() // when the program exits, call the wait method here 
				return
			}
		}
	}()

	return nil
}

```

When I start this demo func in the web service, the ctx1 of this demo has not been cancelled. Here we use the wrap method as a callback function. The internal waitgroup is only doing Add(1), Done() operations, please pay attention to me The way it is used in this way. When I was doing pprof analysis, I found that sync block and blocking syscall are more serious indicators. Is there a problem when I use waitgroup like this? 
In a concurrent scenario, will the mixed use of waitgroup and goroutine cause the program to be abnormal or hang up? 