---
date created: Sunday, July 23rd 2023, 10:34:52 am
date modified: Sunday, July 23rd 2023, 10:36:35 am
tags:
  - dpkg
  - apt
---

# dpkg

## print architecture

this will give you something like `arm64`  and might be better than using `uname -m` for some automation scripts, which often prints out `aarch64`

```shell
dpkg --print-architecture
```
