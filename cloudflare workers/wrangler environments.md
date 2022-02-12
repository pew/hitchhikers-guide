# wrangler environments

have a custom route but want to do testing on a `.workers.dev` domain? add this to your `wrangler.toml`:

```
[env.dev]
workers_dev = true
```

you can run it like so then (with the `-e` flag):

```
wrangler dev -e dev
```