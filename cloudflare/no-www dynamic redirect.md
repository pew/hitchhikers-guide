---
date created: Wednesday, September 6th 2023, 11:57:04 am
date modified: Wednesday, September 6th 2023, 12:03:53 pm
tags:
  - cloudflare
  - redirect
---

# no-www dynamic redirect

- [dynamic redirect docs](https://developers.cloudflare.com/rules/url-forwarding/)

to redirect from www. to the non-www host using **dynamic redirects** instead of page rules:

1. create a new dynamic redirect rule
2. *When incoming requests match…* click the *edit expression* box and paste the following (your www. hostname)

```
(http.host eq "www.example.com")
```

3. *Then...* select *Dynamic* as the redirect *Type* the following expression and *301* as the *Status Code*

```
concat("https://example.com", http.request.uri)
```

4. you can also tick the box *Preserve query string*
