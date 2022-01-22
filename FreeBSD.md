# Go on FreeBSD

| **Kernel version** | **Architectures** | **Initial support version** | **Final support version** |
|:-------------------|:------------------|:----------------------------|:--------------------------|
| 13-STABLE          | amd64, arm, 386   | _**_                        |                           |
| 12-STABLE          | amd64, arm, 386   | Go 1.12 _**_                |                           |
| 11-STABLE          | amd64, arm, 386   | Go 1.7                      |                           |
| 10-STABLE (EOL)    | amd64, arm, 386   | Go 1.3 _*_                  | Go 1.12.4                 |
| 9-STABLE (EOL)     | amd64, 386        | Go 1 _*_                    | Go 1.9.7                  |
| 8-STABLE (EOL)     | amd64, 386        | Go 1 _*_                    | Go 1.9.7                  |
| 7-STABLE (EOL)     | amd64, 386        | Go 1                        | Go 1.1.2                  |

_*_ Go 1.5 or above is recommended.

_**_ FreeBSD 12/13 requires a kernel with `options COMPAT_FREEBSD11` config (this is the default). 64-bit inode aware system calls are available since https://go.dev/cl/143637. See https://go.dev/issues/22447.