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

## cut video

just take the first 28 seconds, beginning at 0:

```
ffmpeg -ss 00:00:00.0 -to 00:00:28.0 -i input.mp4 outpu4.mp4
```

## merge / concat mp3 files

concatenate multiple audio files into one big one.

```shell
ffmpeg -i "concat:file1.mp3|file2.mp3" -acodec copy output.mp3
```

if you want to do this for a bunch of files in a folder

```shell
echo -n "ffmpeg -i \"concat:"; for i in *.mp3;do printf "%s${i}|";done;echo -n "\" -acodec copy output.mp3"
```

this will just spit out the ffmpeg command, for double checking, you know.

## extract audio from video

```
ffmpeg -i input-video.mov -q:a 0 -map a output-audio.mp3
```

## compress video

to 1.5mbps

```
ffmpeg -i IMG_4329.mov -c:v libx264 -b:v 1.5M -c:a aac -b:a 128k meshtastic.mp4
```
