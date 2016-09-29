# Go on NetBSD

| **Kernel version** | **Architectures** | **Min. version** | **Max. version** |
|:-------------------|:------------------|:-----------------|:-----------------|
| 7.0                | amd64, arm, 386   | go1.3 _*_        | go1.7            |
| 6.1                | amd64, arm, 386   | go1.3 _*_        | go1.7            |
| 6.0                | amd64, arm, 386   | go1.3 _*_        | go1.7            |
| 5.0                | amd64, 386        | go1              | go1.2            |
 _*_ Go 1.5 or above is recommended.

# Preparing NetBSD for Go
  * install NetBSD 6.0 (remember to install pkgsrc in the last step)
  * install shells/bash and devel/git (do ` make package-install clean ` in ` /usr/pkgsrc/shells/bash ` and ` /usr/pkgsrc/devel/git `.
    * Using binary packages: ` pkgin install bash git `