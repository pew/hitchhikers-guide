---
date created: Saturday, June 1st 2024, 1:10:14 pm
date modified: Saturday, June 1st 2024, 1:15:26 pm
tags:
  - mdfind
  - mdutil
  - spotlight
  - macos
  - tmutil
---

# tmutil - time machine utility

see also:

- [mdutil](mdutil.md) - manage the metadata stores used by Spotlight
- [asimov](asimov.md)

## remove time machine exclusion

```shell
tmutil removeexclusion /path/to/directory # or file
```

## bulk remove time machine exclusions

example: for some reason, I had a long list of files excluded which were stored in my iCloud Drive, and I didn't know why. the files contained spaces as well and need to be treated differently.

1. find all files which are excluded by time machine, I'm filtering the files which are stored in iCloud Drive (apple's great name for this folder is `com~apple~CloudDocs`)
2. change the `IFS` variable to not treat spaces as an input separator, but rather newlines
3. iterate through the files (**check the output file before doing this**) and remove the time machine exclusion entry for entry

```shell
sudo mdfind "com_apple_backup_excludeItem = 'com.apple.backupd'"|rg "com~apple~CloudDocs" > $TMPDIR/exclude.txt
IFS=$'\n'
for i in $(cat $TMPDIR/exclude.txt); do tmutil removeexclusion "$i";done
```
