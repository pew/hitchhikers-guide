# youtube-dl

[youtube-dl](https://ytdl-org.github.io/youtube-dl/) is a nice little tool to download videos and audio from youtube and millions of other sites.

## download playlist with correct numbering

like 01, 02, 03 and so on.

```
youtube-dl -o "%(autonumber)s-%(title)s.%(ext)s" <URL-HERE>
```

## download mp4 format

```
youtube-dl -f mp4
```
