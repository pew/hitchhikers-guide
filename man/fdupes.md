---
date created: Saturday, January 28th 2023, 1:44:51 pm
date modified: Saturday, January 28th 2023, 1:44:53 pm
tags: 
  - fdupes
---

# fdupes

... find (and delete) duplicate files

## find duplicate files

```shell
fdupes . # current folder
fdupes /path/to/folder # some other folder
fdupes /path1 /path2 # compare two folders
```

## delete duplicates

**without** a prompt:

```shell
fdupes -d -N .
```

**ask** which ones should be deleted:

```shell
fdupes -d .
```