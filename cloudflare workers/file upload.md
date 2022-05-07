---
tags: 
date created: Friday, January 28th 2022, 6:03:12 am
date modified: Saturday, May 7th 2022, 6:57:03 am
title: file upload
---

# file upload

…upload some binary files, or some cute cat and dog images and photos.

Take file, save it as an `arrayBuffer` and put the mime type into Cloudflare Worker's KV metadata field.

the example below takes a GET request with the query string `image` to retrieve the data from KV (including the metadata as `content-type`) and takes a `POST` request against the `/upload` path. you can upload files like so with curl:

```
curl -F file=@image.png https://your-worker.script.workers.dev/upload
```

and fetch it like so then in your browser: `https://your-worker.script.workers.dev/?image=image.png`

```javascript
async function handleRequest(request, env) {
  const { searchParams, pathname } = new URL(request.url)
  let image = searchParams.get('image')

  if (image) {
    const img = await env.images.getWithMetadata(image, { type: 'arrayBuffer' })
    return new Response(img.value, { headers: { 'content-type': img.metadata.filetype } })
  }

  if (pathname === '/upload' && request.method === 'POST') {
    const formData = await request.formData()
    const file = formData.get('file')
    await env.images.put(file.name, await file.arrayBuffer(), { metadata: { filetype: file.type } })
    return new Response(JSON.stringify({ name: file.name, type: file.type, size: file.size }))
  }
}

export default {
  async fetch(request, env) {
    try {
      return await handleRequest(request, env)
    } catch (e) {
      return new Response(e.message)
    }
  },
}
```

## large file upload

here's an example function to upload large bits of files, the whole body without running into a timeout or anything like that. Keep in mind that the maximum file size is still limited by whatever MB/GB is set to your account.

```typescript
export async function putFile(request: Request, env: any): Promise<Response> {
  const contentType = request.headers.get('content-type')
  const filename = crypto.randomUUID()

  if (request.method === 'POST') {
    try {
      await env.bucket.put(filename, request.body, {
        httpMetadata: {
          contentType: contentType,
        },
      })
      return new Response(JSON.stringify({ success: true, filename: filename }))
    } catch (error) {
      return new Response(JSON.stringify({ success: false, message: 'could not upload file', error: error }))
    }
  }
}
```

how to upload this with curl then, the important bit is the `Transfer-Encoding: chunked`, and for large files or low-memory systems you need to use `-T` for uploading since `--data-binary` would load the whole file into memory. Also, set the `content-type` or get it through other means from your code:

```shell
curl -H "Transfer-Encoding: chunked" -H "content-type: video/mp4" --data-binary @example.mp4 https://example.com/r2/upload
curl -H "Transfer-Encoding: chunked" -H "content-type: video/mp4" -T example.mp4 https://example.comv/r2/upload
```
