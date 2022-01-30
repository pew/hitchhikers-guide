#  get query string

it's *just basic JS* stuff, yet I need it in this place.

```javascript
async function handleRequest(request) {
  const { searchParams } = new URL(request.url)
  let name = searchParams.get('name')
  console.log(name)
}
```