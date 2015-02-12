# Rate Limiting

To limit the rate of operations per unit time, use a [time.Ticker](http://golang.org/pkg/time/#NewTicker).
This works well for rates up to 10s per second.
For higher rates, prefer a token bucket rate limiter (search godoc.org for
[rate limit](http://godoc.org/?q=rate+limit)).

```go
import "time"

ratePerSec := 10
throttle := time.Tick(1e9 / ratePerSec)
for req := range requests {
  <-throttle  // rate limit our Service.Method RPCs
  go client.Call("Service.Method", req, ...)
}
```

To allow some bursts, add a buffer to the throttle:
```go
import "time"

ratePerSec := 10
burstLimit := 100
tick := time.NewTicker(1e9 / ratePerSec)
defer tick.Stop()
throttle := make(chan time.Time, burstLimit)
go func() {
  for t := range tick {
    select {
      case: throttle <- t
      default:
    }
  }  // exits after tick.Stop()
}()
for req := range requests {
  <-throttle  // rate limit our Service.Method RPCs
  go client.Call("Service.Method", req, ...)
}
```
