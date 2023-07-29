---
date created: Sunday, July 23rd 2023, 10:34:52 am
date modified: Saturday, July 29th 2023, 10:39:38 am
tags:
  - dpkg
  - apt
  - linux
---

# dpkg

## print architecture

this will give you something like `arm64`  and might be better than using `uname -m` for some automation scripts, which often prints out `aarch64`

```shell
dpkg --print-architecture
```

## get information about a package

```shell
dpkg --info cloudflared.deb
```
