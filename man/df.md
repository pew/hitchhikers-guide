---
date created: Saturday, February 25th 2023, 11:12:23 am
date modified: Saturday, February 25th 2023, 11:14:00 am
tags:
  - df
  - linux
---

# df

## show file system type

```shell
df -T /
df -T /mnt
```

**output:**

```
Filesystem     Type  1K-blocks      Used Available Use% Mounted on
/dev/md0       btrfs 499973440 110767024 383516256  23% /

Filesystem     Type 1K-blocks     Used Available Use% Mounted on
/dev/vda1      ext4  24476576 12632896  10516636  55% /
```
