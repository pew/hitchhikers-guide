# ffmpeg

## get file metadata

```
ffmpeg -i filename.ext
```

**write metadata to a file:**

```
ffmpeg -i filename.mp3 -f ffmetadata metadata.txt
```

## downsample mp3

hopefully make it somewhat smaller

```
ffmpeg -i filename.mp3 -a:b 64k out.mp3
```

**using variable bitrate (vbr):**

[here's a table](https://trac.ffmpeg.org/wiki/Encode/MP3) of the different VBR levels.

```
ffmpeg -i filename.mp3 -q:a 9 out.mp3
```

