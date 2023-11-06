---
date created: Monday, November 6th 2023, 7:07:17 pm
date modified: Monday, November 6th 2023, 7:19:46 pm
tags:
  - rename
---

# rename

## append / prepend numbered sequence

remove `-n` to actually do any renaming

```shell
rename -n -X -N 00001 -e 's/.*/$N/' *.jpg
```

## rename to lowercase

```shell
rename -f 'y/A-Z/a-z/' *
```
