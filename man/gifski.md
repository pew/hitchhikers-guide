---
date created: Saturday, May 3rd 2025, 9:55:05 am
date modified: Saturday, May 3rd 2025, 10:04:28 am
tags:
  - imagemagick
  - gif
  - ffmpeg
---

# gifski

> Highest-quality GIF encoder based on pngquant

- [github project](https://github.com/sindresorhus/Gifski)

see also [ffmpeg](/man/ffmpeg/) and [imagemagick](/man/imagemagick/)

## create small-ish .gif from video

```shell
gifski --quality 70 --fps 10 --width 320 -o output.gif input.mp4
```
