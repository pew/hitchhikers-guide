---
date created: Wednesday, May 18th 2022, 5:11:25 am
date modified: Wednesday, September 21st 2022, 6:52:29 am
tags: 
  - wrangler
  - cloudflare
---

# wrangler

## specify routes

```toml
routes = [{ pattern = "sub.example.com/r2/*", zone_name = "example.com" }]
```

## wrangler environments

have a custom route but want to do testing on a `.workers.dev` domain? add this to your `wrangler.toml`:

```
[env.dev]
workers_dev = true
```

you can run it like so then (with the `-e` flag):

```
wrangler dev -e dev
```

## logs

for Workers:

```shell
wrangler tail
```

for Cloudflare Pages:

```shell
wrangler pages deployment tail
```
