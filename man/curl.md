---
date created: Saturday, April 17th 2021, 7:09:59 am
date modified: Saturday, December 7th 2024, 12:20:41 pm
tags:
  - curl
  - file handling
---

# curl

## force GET request and get headers

If you just want the headers and use `-I`, curl will do a `HEAD` request, so you can force to do a `GET` request:

```shell
curl -X GET -I https://example.com/
```

## --next

run requests after another with a single curl command:

```
curl https://httpbin.org/get --next -X POST --data "abc=xyz" https://httpbin.org/post --next https://httpbin.org/headers
```

[blog post about this](https://daniel.haxx.se/blog/2014/03/12/whats-next-for-curl/), [source](https://changelog.com/news/a3Ep/visit)

## use socks proxy

the example below uses the proxy the Tor Browser is exposing when open

```shell
curl -x socks5h://localhost:9150 https://icanhazip.com/
```

## uploading files

### form upload

form upload will include things like a filename and the *content-type*.

```shell
curl -F 'file=@screenshot.png' https://example.com/post
```

### just upload the file

just the body of the file will be uploaded here.

```shell
curl -X PUT -H "content-type: video/mp4" --data-binary '@a54dfef2-3006-4702-8eaa-3f28bee43e1a.mp4' https://example.com/video.mp4
```
