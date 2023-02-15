# Go on FreeBSD

| **Kernel version** | **Architectures**               | **Initial support version** | **Final support version** |
|:-------------------|:--------------------------------|:----------------------------|:--------------------------|
| 14-CURRENT         | amd64, 386, arm, arm64, riscv64 | _**_ _***_                  |                           |
| 13-STABLE          | amd64, 386, arm, arm64, riscv64 | _**_ _***_                  |                           |
| 12-STABLE          | amd64, 386, arm, arm64          | Go 1.12 _**_                |                           |
| 11-STABLE (EOL)    | amd64, 386, arm, 386            | Go 1.7                      | Go 1.19.x                 |
| 10-STABLE (EOL)    | amd64, 386, arm, 386            | Go 1.3 _*_                  | Go 1.12.4                 |
| 9-STABLE (EOL)     | amd64, 386                      | Go 1 _*_                    | Go 1.9.7                  |
| 8-STABLE (EOL)     | amd64, 386                      | Go 1 _*_                    | Go 1.9.7                  |
| 7-STABLE (EOL)     | amd64, 386                      | Go 1                        | Go 1.1.2                  |

_*_ Go 1.5 or above is recommended.

_**_ Go versions prior to 1.20 require a kernel with `options COMPAT_FREEBSD11` config (this is the default). 64-bit inode aware system calls are available since https://go.dev/cl/143637. See https://go.dev/issues/22447.

_***_ Go 1.20 is the first version to support freebsd/riscv64.