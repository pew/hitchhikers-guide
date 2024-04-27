---
date created: Saturday, April 27th 2024, 9:53:49 am
date modified: Saturday, April 27th 2024, 10:00:23 am
tags:
  - rsync
---

# rsync

see also my mess over at [ssh, scp, rsync](ssh,%20scp,%20rsync.md)

## only include specific file (pattern)

I only want to sync files which match a specific name and exclude everything else.

- **Important:** the include/exclude lists are **case sensitive**.

In this case, I want to sync all files with *foo* and *bar* in the name, so it'd match the files *foobar* and *Superduper.jpg*

```shell
rsync -avP --include={*foo*,*Super*} --include='*/' --exclude='*' rsync://example.com/files/ ~/Downloads
```
