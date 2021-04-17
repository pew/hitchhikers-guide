# curl

## --next

run requests after another with a single curl command:

```
curl https://httpbin.org/get --next -X POST --data "abc=xyz" https://httpbin.org/post --next https://httpbin.org/headers
```

[blog post about this](https://daniel.haxx.se/blog/2014/03/12/whats-next-for-curl/), [source](https://changelog.com/news/a3Ep/visit)