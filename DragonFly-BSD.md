# Go on DragonFly BSD

From https://github.com/golang/go/issues/34958#issuecomment-543852995 :

> Go's DragonFly support policy is that we support the latest stable
> release primarily, but also try to keep DragonFly master passing, in
> prep for it to become the latest stable release.
>
> But that does mean we need one more builder at the moment.

| **Kernel version**      | **Architectures** | **Initial support version** | **Final support version** |
|:------------------------|:------------------|:----------------------------|:--------------------------|
| 4.6 or above            | amd64             | Go 1.8                      |                           |
| 4.4.4 (EOL)             | amd64             | Go 1.8                      |                           |
| 4.4 through 4.4.3 (EOL) | amd64             | Go 1.3 _*_                  | Go 1.7.6                  |
| 3.8 through 4.2 (EOL)   | amd64             | Go 1.3 _*_                  | Go 1.7.6                  |
| 3.6 (EOL)               | amd64, 386        | Go 1.3                      | Go 1.4.3                  |

_*_ Go 1.5 or above is recommended.