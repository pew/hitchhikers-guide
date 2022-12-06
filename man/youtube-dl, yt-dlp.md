---
tags:
  - yt-dlp
  - ytdlp
  - youtube-dl
date created: Tuesday, April 9th 2019, 4:37:46 pm
date modified: Wednesday, May 18th 2022, 5:52:08 am
title: 'youtube-dl, yt-dlp'
---

# youtube-dl, yt-dlp

[youtube-dl](https://ytdl-org.github.io/youtube-dl/) is a nice little tool to download videos and audio from youtube and millions of other sites.

## download playlist with correct numbering

like 01, 02, 03 and so on.

```shell
youtube-dl -o "%(autonumber)s-%(title)s.%(ext)s" <URL-HERE>
```

## download mp4 format

```shell
youtube-dl -f mp4
```

## download best video format with mp4 extension

```shell
yt-dlp -f "best[ext=mp4]" LpDqomAHSlQ
```

## download embedded videos

e.G. vimeo videos embedded as an iframe, send a referer with the request:

```
youtube-dl "https://player.vimeo.com/video/1234" --referer "https://example.com/where-you-found-that-page/"
```

## extract audio

... and remove ads

```shell
yt-dlp --sponsorblock-remove all -x --audio-format mp3 https://example.com/
```
