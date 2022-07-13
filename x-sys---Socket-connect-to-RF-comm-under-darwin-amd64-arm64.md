I have a working example for the socket connection which is based on linux/unix system. But when I wanted to build it for darwin amd64 I found out that certain parts of my implementation does not exists for darwin amd64 (also for arm64). 

This is the main implementation:
```
import "golang.org/x/sys/unix"
// ...
fd, _ := unix.Socket(unix.AF_BLUETOOTH, unix.SOCK_STREAM, unix.BTPROTO_RFCOMM)
socketAddr := &unix.SockaddrRFCOMM{Addr: str2ba(addr), Channel: 6}
unix.Connect(fd, socketAddr)
```

The missing parts are the `unix.AF_BLUETOOTH`, `unix.BTPROTO_RFCOMM` and the `unix.SockaddrRFCOMM`. I cloned the `github.com/golang/sys` repository to find out whether there is something similar, but I didn't found anything which looks like an RFCOMM on darwin.

Question

Is there anything what I can use to have the same functionality under darwin amd64/arm64? Also if there is any guide/documentation which details it would be awesome.