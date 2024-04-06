---
date created: Tuesday, December 28th 2021, 6:42:59 am
date modified: Saturday, April 6th 2024, 11:55:27 am
tags:
  - tr
---

# tr

## replace newline with comma

```shell
tr '\n' ','
```

## strip newline from input

If you do this and paste it afterwards, it'll add a newline or will even be used as *return* in some forms:

```
head -c 32 /dev/urandom|base64|pbcopy
```

**strip the newline**

do it like this, `tr -d '\n'` is the key:

```
head -c 32 /dev/urandom|base64|tr -d '\n'|pbcopy
```
