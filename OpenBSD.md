# Go on OpenBSD

Go is available within the OpenBSD ports tree collection since OpenBSD 5.2.  It is marked as i386- and amd64- only.  See [`ports/lang/go`](http://ports.su/lang/go) for details.

| **OpenBSD release** | **Go in ports**     |
|:--------------------|:--------------------|
| 6.2 (Oct 9, 2017)   | go-1.9              |
| 6.1 (Apr 11, 2017)  | go-1.8              |
| 6.0 (Sep 1, 2016)   | go-1.6.3            |
| 5.9 (Mar 29, 2016)  | go-1.5.4            |
| 5.8 (Oct 18, 2015)  | go-1.4.2            |
| 5.7 (May 1, 2015)   | go-1.4.1            |
| 5.6 (Nov 1, 2014)   | go-1.3p0            |

## Building from source

| **Kernel version** | **Architectures** | **Initial support version** | **Final support version** |
|:-------------------|:------------------|:----------------------------|:--------------------------|
| 6.4                | amd64, arm, 386   | Go 1.11                     |                           |
| 6.2 through 6.3    | amd64, arm, 386   | Go 1.9                      |                           |
| 6.1                | amd64, arm, 386   | Go 1.8                      | Go 1.10.5                 |
| 6.0                | amd64, 386        | Go 1.4.1 _*_                | Go 1.10.5                 |
| 6.0                | arm               | Go 1.5                      | Go 1.10.5                 |
| 5.9                | amd64, 386        | Go 1.4.1 _*_                | Go 1.8.7                  |
| 5.9                | arm               | Go 1.5                      | Go 1.8.7                  |
| 5.6 through 5.8    | amd64, 386        | Go 1.4.1 _*_                | Go 1.7.6                  |
| 5.5                | amd64, 386        | Go 1.3 _*_                  | Go 1.7.6                  |
| 5.0 through 5.4    | amd64, 386        | Go 1                        | Go 1.2.2                  |

_*_ Go 1.5 or above is recommended.

## Longterm support

Go aims to support the two most recent OpenBSD releases, because OpenBSD officially supports only the two most recent releases, and makes a best-effort attempt to maintain ABI support in consecutive releases.

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