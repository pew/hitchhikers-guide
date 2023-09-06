---
date created: Tuesday, September 20th 2022, 8:02:34 pm
date modified: Wednesday, September 21st 2022, 6:52:26 am
tags:
  - cloudflare
  - workers
  - r2
---

# r2 file upload

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
curl -X PUT -H "content-type: video/mp4" -d @abc.mp4 https://r2.example.com/
```
