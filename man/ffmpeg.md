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
