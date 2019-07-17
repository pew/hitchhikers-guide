# reddit

ehm... okay?

## get markdown version of reddit post

you need *jq* for this, at least it makes it easy.

```
curl -sS -A "Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:59.0) Gecko/20100101 Firefox/59.0" https://www.reddit.com/r/subreddit/comments/someid/text.json | jq -r '.[].data.children[].data.selftext'
```
