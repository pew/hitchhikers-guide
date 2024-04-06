---
date created: Saturday, April 6th 2024, 11:02:59 am
date modified: Saturday, April 6th 2024, 11:04:11 am
tags:
  - macos
  - spotlight
  - mdutil
---

# mdutil

the command line utility to manage macOS Spotlight search

## check spotlight index status

check for all devices:

```shell
mdutil -avs
```

check specific device:

```shell
mdutil -s -v /
```
