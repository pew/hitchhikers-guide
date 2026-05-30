---
date created: Wednesday, December 25th 2024, 12:37:20 pm
date modified: Wednesday, December 25th 2024, 12:40:11 pm
tags: 
---

# create m3u playlists

tl;dr: m3u playlist files are just a text file with the list of file names

## files in the same directory

```shell
ls -1 *.mp3 > playlist.m3u
```

## current directory and subdirectories

```shell
find . -type f -iname "*.mp3" | sort > playlist.m3u
```

## absolute paths

```shell
find "$(pwd)" -type f -iname "*.mp3" | sort > playlist.m3u
```
