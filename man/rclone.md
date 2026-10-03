---
date created: Saturday, October 3rd 2026, 8:49:13 am
date modified: Saturday, October 3rd 2026, 8:53:25 am
tags:
  - rclone
  - rsync
  - backup
---

# rclone

[rclone](https://rclone.org/) is a handy CLI tool for syncing, copying, and managing files across cloud storage providers and local filesystems

## server to server streaming for large files

… in a way that they're eventually uploaded successfully. example, copy from a **http source** to a cloudflare **r2 (s3) bucket**:

```shell
rclone copyto \
  --http-url 'https://data.example.com/' \ # just put the host
  ':http:files/huge-file.tar' \ # put the path to the file
  'r2:assets/huge-file.tar' \ # this is the configured rclone destination
  --multi-thread-streams 8 \
  --multi-thread-cutoff 64M \
  --s3-chunk-size 64M \
  --s3-upload-concurrency 8 \
  --s3-no-check-bucket \
  --disable-http2 \
  -P -vv
```
