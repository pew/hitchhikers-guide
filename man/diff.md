---
date created: Friday, December 27th 2024, 11:01:17 am
date modified: Friday, December 27th 2024, 11:05:51 am
tags:
  - diff
  - vimdiff
---

# diff

## compare files

- **side-by-side comparison**: `diff -y file1 file2`
- **unified format**: `diff -u file1 file2`
- **ignore whitespace differences**: `diff -w file1 file2`

## merge files

### vimdiff

- Use `dp` (put changes) and `do` (get changes) to merge

```shell
vimdiff file1 file2
```

- sometimes, vimdiff copies more than you want, try the following:

```shell
:diffget . 
#:diffput .
```

if you get `more than one match for .`, mark the whole line with `v` and use `:diffget`

### sdiff

- step-by-step side-by-side merging:

```shell
sdiff -o mergedfile file1 file2
```
