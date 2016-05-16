# Go on OpenBSD

Go is available within the OpenBSD ports tree collection since OpenBSD 5.2.  It is marked as i386- and amd64- only.  See [`ports/lang/go`](http://ports.su/lang/go) for details.

| **OpenBSD release** | **golang in ports** |
|:--------------------|:--------------------|
| 5.9 (Mar 29, 2016)  | go-1.5.4            |
| 5.8 (Oct 18, 2015)  | go-1.4.2            |
| 5.7 (May 1, 2015)   | go-1.4.1            |
| 5.6 (Nov 1, 2014)   | go-1.3p0            |

## Building from source.

Required:

  * OpenBSD amd64, 386: 5.6 and above
    * If you want to run go1.3 or 1.4 on OpenBSD 5.6, see http://golang.org/issue/9102

| **Kernel version** | **Min. version** | **Max. version**|
|:-------------------|:-----------------|:----------------|
| 5.9                | go1.4.1          | go1.7 |
| 5.8                | go1.4.1          | go1.7 |
| 5.7                | go1.4.1          | go1.7 |
| 5.6                | go1.4.1          | go1.7 |

  * ulimits (` /etc/login.conf `)

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