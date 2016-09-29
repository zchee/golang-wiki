# Go on OpenBSD

Go is available within the OpenBSD ports tree collection since OpenBSD 5.2.  It is marked as i386- and amd64- only.  See [`ports/lang/go`](http://ports.su/lang/go) for details.

| **OpenBSD release** | **golang in ports** |
|:--------------------|:--------------------|
| 6.0 (Sep 1, 2016)   | go-1.6.3            |
| 5.9 (Mar 29, 2016)  | go-1.5.4            |
| 5.8 (Oct 18, 2015)  | go-1.4.2            |
| 5.7 (May 1, 2015)   | go-1.4.1            |
| 5.6 (Nov 1, 2014)   | go-1.3p0            |

## Building from source

| **Kernel version** | **Architectures** | **Min. version** | **Max. version** |
|:-------------------|:------------------|:-----------------|:-----------------|
| 6.0                | amd64, 386        | go1.4.1 _*_      | go1.7            |
| 6.0                | arm               | go1.5            | go1.7            |
| 5.9                | amd64, 386        | go1.4.1 _*_      | go1.7            |
| 5.9                | arm               | go1.5            | go1.7            |
| 5.8                | amd64, 386        | go1.4.1 _*_      | go1.7            |
| 5.7                | amd64, 386        | go1.4.1 _*_      | go1.7            |
| 5.6                | amd64, 386        | go1.4.1 _*_      | go1.7            |
| 5.5                | amd64, 386        | go1.3            | go1.7            |
| 5.0 through 5.4    | amd64, 386        | go1              | go1.2            |
_*_ If you want to run Go 1.3 or 1.4 on OpenBSD 5.6 or above, see http://golang.org/issue/9102.

## ulimits (` /etc/login.conf `)

Edit `/etc/login.conf` so that the staff class has the proper
settings. The following is a working example of the staff class:
```
staff:\
       :datasize-cur=infinity:\
       :datasize-max=infinity:\
       :datasize=infinity:\
       :openfiles-cur=4096:\
       :maxproc-max=512:\
       :maxproc-cur=512:\
       :ignorenologin:\
       :requirehome@:\
       :tc=default:
```

If the database file `/etc/login.conf.db` exists, you need to rebuild it with:
```
# cap_mkdb /etc/login.conf
```

Ensure that the user you intend to build Go with is in the `staff` login class:
```
# usermod -L staff your_username_here
```