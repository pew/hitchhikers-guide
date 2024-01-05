---
date created: Saturday, January 5th 2019, 9:06:46 am
date modified: Friday, January 5th 2024, 5:44:56 am
tags:
  - linux
---

# lsblk

## drive info

easy way, get the fstype, uuid etc.:

```shell
lsblk -f
```

you can combine most commands, like `NAME,UUID,LABEL`

### get UUID

if you want to set some permanent settings, don't use `/dev/sda` and so on if they change, use the UUID or label.

```
lsblk -o NAME,UUID
```

### get LABEL

```
lsblk -o NAME,LABEL
```
