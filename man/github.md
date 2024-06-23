---
date created: Sunday, December 25th 2022, 9:53:21 am
date modified: Sunday, June 23rd 2024, 10:25:11 am
tags:
  - github
---

# github

see also [github actions](github%20actions.md) and [gh](gh.md) for more GitHub related things

## download latest release

if the filenames easy enough, you can just do this:

```shell
curl -OL https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm
```

or use the github api to list all released assets:

```shell
curl -sL https://api.github.com/repos/creativeprojects/resticprofile/releases/latest
```

and combine it with `jq`

```shell
curl -sL https://api.github.com/repos/creativeprojects/resticprofile/releases/latest | jq -r ".assets[] | select(.name | contains (\"$(dpkg --print-architecture)\")) | .browser_download_url"
```
