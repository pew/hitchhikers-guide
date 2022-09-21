---
date created: Saturday, February 19th 2022, 4:19:05 pm
date modified: Wednesday, September 21st 2022, 6:52:31 am
tags: 
---

# send custom header to origin

let's say you want to send the bot score to the origin server to serve different content. this will fetch the request and add a `x-botscore` header

```javascript
addEventListener("fetch", (event) => {
  event.respondWith(
    handleRequest(event.request).catch(
      (err) => new Response(err.stack, { status: 500 })
    )
  );
});

async function handleRequest(request) {
  const cf = request.cf  
  request = new Request(request)
  request.headers.append("x-botscore", cf.botManagement.score)
  return fetch(request)
}
```
