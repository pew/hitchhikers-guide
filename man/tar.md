---
date created: Thursday, March 30th 2023, 9:31:39 am
date modified: Friday, April 18th 2025, 5:37:06 am
tags:
  - tar
---

# tar

## extract into different directory

extract into `/tmp`:

```shell
tar xzf abc.tar.gz -C /tmp
```

## exclude files or folders

```shell
tar --exclude *.db -cf syncthing.tar syncthing
```
