# read all headers and cf object

```javascript
export default {
  async fetch(request) {
    const { cf } = request
    const headers = Object.fromEntries(request.headers)
    const resp = { cf, headers }
    return new Response(JSON.stringify(resp, null, 2), { headers: { 'content-type': 'application/json' } })
  },
}
```
