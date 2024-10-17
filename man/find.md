---
date created: Sunday, January 20th 2019, 2:55:43 pm
date modified: Thursday, October 17th 2024, 5:14:10 am
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

## find 0 byte files

… you may want to double check if you actually want to delete them, but I had some conflicts in syncthing and checked for them manually

```
find /data -size 0
```
