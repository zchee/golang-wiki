# Rate Limiting

## Time Tick based Approach

To limit the rate of operations per unit time, use time.Tick:

```
import "time"

rate_per_sec := 10
throttle := time.Tick(1e9 / rate_per_sec)
for req := range requests {
  <-throttle  // rate limit our Service.Method RPCs
  go client.Call("Service.Method", req, ...)
}
```

To allow some bursts, add a buffer to the throttle:
```
import "time"

rate_per_sec := 10
burst_limit := 100
tick := time.NewTicker(1e9 / rate_per_sec)
defer tick.Stop()
throttle := make(chan int64, burst_limit)
go func() {
  for ns := range tick {
    select {
      case: throttle <- ns
      default:
    }
  }  // exits after tick.Stop()
}()
for req := range requests {
  <-throttle  // rate limit our Service.Method RPCs
  go client.Call("Service.Method", req, ...)
}
```

## Simpler Approach that doesn't need channels or go routines

Here is a simpler approach that relies on the notion of elapsed time to provide rate control. It is implemented as a package so others can readily use it.



```
//
// Ratelimiting incoming connections - Small Library
//
// (c) 2013 Sudhi Herle <sudhi-dot-herle-at-gmail-com>
//
// License: GPLv2
//
// Notes:
//  - This is a very simple interface for rate limiting. It
//    implements a token bucket algorithm
//  - Based on Anti Huimaa's very clever token bucket algorithm.
//
// Usage:
//    rl = NewRateLimiter(rate)
//
//    ....
//    if rl.Limit() {
//       drop_connection(conn)
//    }
//
package ratelimit

import "time"

type Ratelimiter struct {
	rate int       // conn/sec
	last time.Time // last time we were polled/asked

	allowance float64
}

// Create new rate limiter that limits at rate/sec
func NewRateLimiter(rate int) (*Ratelimiter, error) {

	r := Ratelimiter{rate: rate, last: time.Now()}

	r.allowance = float64(r.rate)
	return &r, nil
}

// Return true if the current call exceeds the set rate, false
// otherwise
func (r *Ratelimiter) Limit() bool {

	// handle cases where rate in config file is unset - defaulting
	// to "0" (unlimited)
	if r.rate == 0 {
		return false
	}

	rate := float64(r.rate)
	now := time.Now()
	elapsed := now.Sub(r.last)
	r.last = now
	r.allowance += float64(elapsed) * rate

	// Clamp number of tokens in the bucket. Don't let it get
	// unboundedly large
	if r.allowance > rate {
		r.allowance = rate
	}

	var ret bool

	if r.allowance < 1.0 {
		ret = true
	} else {
		r.allowance -= 1.0
		ret = false
	}

	return ret
}
```

Using this package is quite easy:

```
    // rate limit at 100/s
    nl = ratelimit.NewRateLimiter(100)

    ....
   // in your event loop or network accept loop, do:
   if rl.Limit() {
       // drop the connection etc.
       // i.e., this new event has exceeded the rate of 100/s
    ... 
   }
   else {
      // .. rate is not exceeded, process as needed
      ...
    }
```

[Anti Huimaa](http://stackoverflow.com/questions/667508/whats-a-good-rate-limiting-algorithm) came up with this simple algorithm.

# References

time.Tick: http://golang.org/pkg/time/#Tick