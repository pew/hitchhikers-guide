---
date created: Saturday, April 6th 2024, 11:02:59 am
date modified: Saturday, June 1st 2024, 1:11:59 pm
tags:
  - macos
  - spotlight
  - mdutil
  - mdfind
  - tmutil
---

# mdutil - manage the metadata stores used by Spotlight

the command line utility to manage macOS Spotlight search. see also:

- [tmutil](tmutil.md)
- [asimov](asimov.md)

## check spotlight index status

check for all devices:

```shell
mdutil -avs
```

check specific device:

```shell
mdutil -s -v /
```

## find excluded files by time machine

```shell
sudo mdfind "com_apple_backup_excludeItem = 'com.apple.backupd'"
```
