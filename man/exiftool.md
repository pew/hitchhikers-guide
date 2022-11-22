---
title: exiftool
tags:
  - exiftool
  - metadata
  - security
  - privacy
date created: 2022-11-22
---

# exiftool

exiftool - Read and write meta information in files

## remove metadata from images / videos / media files

this removes all metadta from images and videos etc., it'll create a copy of the original.

```shell
exiftool -all= image.png
```

if you want to override the existing file:

```shell
exiftool -overwrite_original -all= image.png
```
