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