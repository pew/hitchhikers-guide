---
tags: 
  - cloudflare
  - cloudflare workers
  - r2
date created: Tuesday, September 20th 2022, 8:02:34 pm
date modified: Tuesday, September 20th 2022, 8:04:04 pm
---

# workers r2 upload

… put a file into r2 through a Worker:

```typescript
const filename = crypto.randomUUID()
const uploadedObject = await env.bucketName.put(filename, request.body, {
  httpMetadata: request.headers,
})
return new Response(filename, { headers: { etag: uploadedObject?.httpEtag } })
```

then upload with curl like so:

```shell
curl -X PUT -d @abc.mp4 https://r2.example.com/
```
