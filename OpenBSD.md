# Go on OpenBSD

Go is available within the OpenBSD ports tree collection since OpenBSD 5.2.  See [`ports/lang/go`](http://ports.su/lang/go) for details.

| **OpenBSD release** | **golang in ports** |
|:--------------------|:--------------------|
| 5.6                 | go1.3               |
| 5.5                 | go1.2               |
| 5.4                 | go1.1.1             |
| 5.3                 | go1.0.3             |
| 5.2                 | go1.0.2             |

## Building from source.

Required:

  * OpenBSD amd64, 386: 5.5 and above
    * If you want to run go1.3 or 1.4 on OpenBSD 5.6, see http://golang.org/issue/9102

| **Kernel version** | **Min. version** | **Max. version**|
|:-------------------|:-----------------|:----------------|
| 5.6                | go1.4.1          | go1.5 |
| 5.5                | go1.3            | go1.5 |

  * ulimits (` /etc/login.conf `)

Edit the /etc/login.conf so that the staff class has the proper
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

After editing the login.conf you'll need to rebuild the database with:
```
# cap_mkdb /etc/login.conf
```

```
ulimit -n 512
ulimit -p 512
ulimit -d 2036792
```

Add the login class to the user you would like to have build go
```
# vipw
```

Look for the 5th element which is the login class, this is blank by
users added by useradd. In the following example the user operator
would be added to the staff class
```
## Before
operator:*:2:5::0:0:System &:/operator:/sbin/nologin

## After
operator:*:2:5:staff:0:0:System &:/operator:/sbin/nologin
```

## Under KVM

If under KVM on Lucid, you don't need to disable ` mpbios `, but the OpenBSD kernel spins at takes nearly 100% CPU if you don't.  So, see:

http://scie.nti.st/2009/10/4/running-openbsd-4-5-in-kvm-on-ubuntu-linux-9-04

Nutshell:

```
# config -ef /bsd
OpenBSD 4.5 (GENERIC) #2052: Sat Feb 28 14:55:24 MST 2009
    deraadt@amd64.openbsd.org:/usr/src/sys/arch/amd64/compile/GENERIC
Enter 'help' for information
ukc> disable mpbios
 54 mpbios0 disabled
ukc> quit
Saving modified kernel.
#
```
