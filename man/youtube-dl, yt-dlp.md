---
date created: Tuesday, April 9th 2019, 4:37:46 pm
date modified: Monday, January 6th 2025, 10:17:18 am
tags:
  - yt-dlp
  - ytdlp
  - youtube-dl
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

### extract mp3 from soundcloud

requires the `-x` flag

```shell
yt-dlp -x --audio-format mp3 https://example.com/
```

## download podcasts

yt-dlp can also be used as a podcatcher for regular RSS feeds. I'm using this to archive a few podcasts, using the `-o` formatting options they'll be saved into a folder with the podcast name and title + file extension as the filename

```shell
yt-dlp -o "/backup/podcasts/%(playlist)s/%(title)s.%(ext)s" --restrict-filenames --download-archive archive.txt --no-post-overwrites -i https://example.com/feed/podcast/
```

## use cookies from browser

should also work with `chrome` and `safari` instead of `firefox`. [there's more in the docs](https://github.com/yt-dlp/yt-dlp/wiki/FAQ#how-do-i-pass-cookies-to-yt-dlp)

```shell
yt-dlp --cookies-from-browser firefox
```

## use a config file for yt-dlp

you can put the command line arguments in a file and let yt-dlp always use the config file so you don't need to pass the arguments to it. it can then still be combined with other flags such as the `--cookies-from-browser` thing

or use `--ignore-config` to not use the config file, otherwise:

create the folder and file `~/.config/yt-dlp/config` and put your arguments in there, here's my example:

```
# set the output template for filenames
--output "~/Downloads/%(title)s.%(ext)s"

# restrict filenames to ASCII characters
--restrict-filenames

# download the best mp4 video
--format best[ext=mp4]

# continue downloading partially downloaded files
--continue
```
