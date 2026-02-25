---
title: Go on Linux
---

## Baseline requirements

These are the minimum kernel requirements for any Go build.
Some architectures may have a higher version requirement (see below).

| **Kernel version** | **Final support version** |
| :----------------- | :------------------------ |
| 3.2 or above       |                           |
| 2.6.32 or above    | Go 1.23.12                |
| 2.6.23 or above    | Go 1.18.10                |

## Achitecture-specific requirements

| **Architecture**      | **Kernel version**           | **Initial support version** | **Final support version** |
| :-------------------- | :-----------------           | :-------------------------- | :------------------------ |
| 386                   | 3.2 or above                 | Go 1 _\*_                   |                           |
| amd64                 | 3.2 or above                 | Go 1 _\*_                   |                           |
| arm                   | 3.2 or above                 | Go 1.1 _\*_                 |                           |
| arm                   | 3.1 or above                 | Go 1.1 _\*_                 | Go 1.23.12                |
| arm64                 | TBD                          | Go 1.5                      |                           |
| loong64               | 5.19 or above                | Go 1.19                     |                           |
| mips                  | TBD                          | Go 1.8                      |                           |
| mipsle                | TBD                          | Go 1.8                      |                           |
| mips64                | TBD                          | Go 1.6                      |                           |
| mips64le              | [4.8 or above](/issue/16848) | Go 1.6                      |                           |
| ppc64                 | TBD                          | Go 1.5                      |                           |
| ppc64le               | TBD                          | Go 1.5                      |                           |
| riscv                 | TBD                          | Go 1.14                     |                           |
| s390x                 | TBD                          | Go 1.7                      |                           |

_\*_ Go 1.5 or above is recommended.
