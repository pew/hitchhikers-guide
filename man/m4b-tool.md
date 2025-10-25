---
date created: Friday, June 6th 2025, 4:44:16 pm
date modified: Saturday, October 25th 2025, 11:03:26 am
tags: 
---

# m4b-tool

[m4b-tool is a command line utility to merge, split and chapterize audiobook files such as mp3, ogg, flac, m4a or m4b](https://github.com/sandreas/m4b-tool)

## parallel m4b-tool jobs

use the `--jobs` flag to run conversions in parallel

```shell
m4b-tool merge -v --jobs=4
```

## convert a folder of mp3 to m4b

…using docker:

- it'll mount the current folder into `/input/` and will save the m4b file in `/mnt/media/audiobooks`

```shell
docker run -it --rm -v "$(pwd)"/:/input/ -v /mnt/media/audiobooks/:/output/ sandreas/m4b-tool merge -v /input/ --output-file="/output/filename.m4b"
```

## convert a bunch of folders with mp3 files to m4b

do the same as above, just with a bunch of folders. assuming you're in `/data` with multiple subfolders containing mp3 files:

```shell
for i in *; do docker run -it --rm -v "$(pwd)/$i"/:/input/ -v /mnt/media/audiobooks/:/output/ sandreas/m4b-tool merge -v /input/ --output-file="/output/$i.m4b"; done
```
