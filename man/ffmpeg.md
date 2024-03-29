---
date created: Friday, July 3rd 2020, 7:52:48 pm
date modified: Saturday, March 23rd 2024, 5:11:03 pm
tags:
  - ffmpeg
  - ffprobe
---

# ffmpeg

## compress video

using a quick preset:

```shell
ffmpeg -i input.mov -vcodec libx264 -crf 22 -preset ultrafast -c:a copy output.mp4
```

to 1.5mbps

```shell
ffmpeg -i IMG_4329.mov -c:v libx264 -b:v 1.5M -c:a aac -b:a 128k meshtastic.mp4
```

## convert video from to, e.G.: .flv to .mp4

```shell
ffmpeg -i input.flv -c copy output.mp4
for i in *.flv; do ffmpeg -i "$i" -c copy "${i%.flv}.mp4"; done
```

it might be required to encode the audio separately:

```shell
ffmpeg -i input.flv -c:v copy -c:a aac output.mp4
for i in *.flv; do ffmpeg -i "$i" -c:v copy -c:a aac "${i%.flv}.mp4"; done
```

## cut video

just take the first 28 seconds, beginning at 0:

```
ffmpeg -ss 00:00:00.0 -to 00:00:28.0 -i input.mp4 outpu4.mp4
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

## extract audio from video

```
ffmpeg -i input-video.mov -q:a 0 -map a output-audio.mp3
```

## generate gif from video

endless loop:

```shell
ffmpeg -i in.mp4 -loop 0 out.gif
```

## get file metadata

```
ffmpeg -i filename.ext
```

**write metadata to a file:**

```
ffmpeg -i filename.mp3 -f ffmetadata metadata.txt
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

## video information

```code
ffprobe -show_streams -select_streams v -i input-video.mp4
```

just get the  bitrate (in kbps):

```code
ffprobe -v error -select_streams v:0 -show_entries stream=bit_rate -of default=noprint_wrappers=1:nokey=1 your-video.mp4
```
