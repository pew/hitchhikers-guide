---
date created: Saturday, April 27th 2024, 9:53:49 am
date modified: Saturday, September 7th 2024, 9:44:22 am
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
rsync -avP --include={*/,*foo*,*Super*} --exclude='*' rsync://example.com/files/ ~/Downloads
```

or with individual `include` arguments:

```shell
rsync -avP --include='*.yaml' --include='*.yml' --include='.env' --exclude='.git' --exclude='*' ~/source/ ~/dest/
```

## do not copy empty directories

`-m` or `--prune-empty-dirs`: Prevents rsync from creating empty directories in the destination.

```shell
rsync -avPm ~/source ~/dest
```
