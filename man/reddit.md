---
date created: Wednesday, July 17th 2019, 3:38:37 pm
date modified: Tuesday, February 11th 2025, 5:52:09 am
tags: 
---

# reddit

ehm... okay?

## get json for reddit post

append `.json` to the end of a reddit url

## get text for each reddit comment

```shell
jq -r '.[].data.children[].data | select(.body != null) | "---\n\(.body)"' < reddit.json
```

## get markdown version of reddit post

you need *jq* for this, at least it makes it easy.

```shell
REDDIT_URL=https://www.reddit.com/r/hetzner/comments/asdffoo/title_foobar/
curl -sS -A "Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:59.0) Gecko/20100101 Firefox/59.0" "${REDDIT_URL%/}.json" | jq -r '.[].data.children[].data.selftext' | grep -v null
```
