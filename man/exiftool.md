---
date created: Saturday, June 17th 2023, 6:43:26 am
date modified: Wednesday, January 7th 2026, 9:28:21 am
tags:
  - exiftool
  - metadata
  - security
  - privacy
title: exiftool
---

# exiftool

exiftool - Read and write meta information in files

- see also [qpdf](/man/qpdf/) for manipulating pdf files

## remove metadata from images / videos / media files

this removes all metadta from images and videos etc., it'll create a copy of the original.

**keep orientation / rotation:**

```shell
exiftool -all:all= -tagsfromfile @ -exif:Orientation image.png
```

overwrite orignal image:

```shell
exiftool -overwrite_original -all:all= -tagsfromfile @ -exif:Orientation image.png
```

[source](https://photo.stackexchange.com/a/119646)

**remove everything:**

```shell
exiftool -all= image.png
```

if you want to overwrite the existing file:

```shell
exiftool -overwrite_original -all= image.png
```
