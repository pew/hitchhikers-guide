---
date created: Friday, January 28th 2022, 6:01:54 am
date modified: Wednesday, September 21st 2022, 6:52:27 am
tags: 
---

#  get query string

it's *just basic JS* stuff, yet I need it in this place.

```javascript
async function handleRequest(request) {
  const { searchParams } = new URL(request.url)
  let name = searchParams.get('name')
  console.log(name)
}
```
