---
date created: Saturday, January 3rd 2026, 9:47:39 am
date modified: Saturday, January 3rd 2026, 10:33:56 am
tags:
  - fclones
  - dedupe
  - filesystem
---

# fclones

- [GitHub - pkolaczk/fclones: Efficient Duplicate File Finder](https://github.com/pkolaczk/fclones)

## group duplicates

find duplicate files across single or multiple folders

```shell
fclones group /mnt/media/
fclones group /mnt/bucket-a/ /data/bucket-c/
```

## generate duplicate report

```shell
fclones group /mnt/media/ > dupes.txt
```

## dedupe duplicates

instead of deleting one or the other duplicate file, you can dedupe them using fclones: \[dedupe] *does not remove any files, but deduplicates file data by using native copy-on-write capabilities of the file system (reflink)*

```shell
fclones dedupe < dupes.txt
```
