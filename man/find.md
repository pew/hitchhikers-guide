---
date created: Sunday, January 20th 2019, 2:55:43 pm
date modified: Tuesday, March 18th 2025, 5:43:07 am
tags: 
---

# find

## move files

```shell
find . -type f -print0 | xargs -0 -I {} mv {} dest/path
```

## search depth

to stay in the current folder when searching, use `-d` for the depth, or change it to search through more levels of directories:

```shell
find . -type f -d 1
```

## find incomplete / dead rsync transfers

find them:

```
find /mnt/media/ -type f -iname ".*.*.??????" -ls
```

delete them:

```
find /mnt/media/ -type f -iname ".*.*.??????" -delete
```

## delete files that don't match pattern

assuming you have a folder full of files and you only want to **keep** all files starting with `us-` and `ca-` and delete all others:

```shell
find . -type f ! -name 'us-*' ! -name 'ca-*' -print0 | xargs -0 rm
```

## find 0 byte files

… you may want to double check if you actually want to delete them, but I had some conflicts in syncthing and checked for them manually

```
find /data -size 0
```

## find files older than `n`

files changed in the last day:

```shell
find . -mtime -1
```

files older than 365 days:

```shell
find ~/Library/Preferences -mtime +365
```

you can also add time units `+365h`:

```
s       second
m       minute (60 seconds)
h       hour (60 minutes)
d       day (24 hours)
w       week (7 days)
```
