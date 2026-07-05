---
date created: Monday, November 6th 2023, 7:07:17 pm
date modified: Sunday, July 5th 2026, 6:20:31 pm
tags:
  - rename
---

# rename

remove `-n` to actually rename things

## 2 digit padding

convert `1.mp3`, `2.mp3` to `01.mp3`, and `02.mp3`

```shell
rename -n 's/^(\d+)(\.mp3)$/sprintf("%02d%s", $1, $2)/e' *.mp3
```

## 3 digit padding

```shell
rename -n 's/^(\d+)(\.mp3)$/sprintf("%03d%s", $1, $2)/e' *.mp3
```

## append / prepend numbered sequence

```shell
rename -n -X -N 00001 -e 's/.*/$N/' *.jpg
```

## rename to lowercase

```shell
rename -f 'y/A-Z/a-z/' *
```

## rename only file extension to lowercase

```shell
rename -f 's/([A-Z]+)$/\L$1/' *
```
