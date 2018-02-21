# Go on NetBSD

Go on NetBSD is not stable as of Go 1.8/Go 1.9. See https://tip.golang.org/doc/go1.9#known_issues and https://github.com/golang/go/issues/20852

| **Kernel version**    | **Architectures** | **Initial support version** | **Final support version** |
|:----------------------|:------------------|:----------------------------|:--------------------------|
| 8.0 or above          | amd64, arm, 386   |                             |                           |
| 7.0 through 7.1       | amd64, arm, 386   | Go 1.3 _*_                  |                           |
| 6.0 through 6.1       | amd64, arm, 386   | Go 1.3 _*_                  |                           |
| 5.0 through 5.2 (EOL) | amd64, 386        | Go 1                        | Go 1.2.2                  |

_*_ Go 1.5 or above is recommended.

# Preparing NetBSD for Go
  * install NetBSD 6.0 (remember to install pkgsrc in the last step)
  * install shells/bash and devel/git (do ` make package-install clean ` in ` /usr/pkgsrc/shells/bash ` and ` /usr/pkgsrc/devel/git `.
    * Using binary packages: ` pkgin install bash git `