---
date created: Tuesday, December 2nd 2025, 5:52:06 am
date modified: Friday, January 9th 2026, 11:20:45 am
tags: 
---

# dig

- [see also DNS](/man/dns)

## dig with dns over tls (DoT) / dns over https (DoH)

you need a more recent version of `dig`, with homebrew you need to run:

```shell
brew install bind
```

which will install `dig`.

### dns over tls (dot)

```shell
dig @1.1.1.1 +tls google.com
```

### dns over https (doh)

```shell
dig @cloudflare-dns.com +https google.com
```

## check if dnssec is enabled

```shell
dig +dnssec +multi example.com
```

## digrc

customize your `dig` output with a config file. Create the file `~/.digrc` for this, and add the following:

```
+noall +answer
```

the above will only show the answer, like so:

```
$ dig man.ilayk.com
man.ilayk.com.		300	IN	CNAME	hitchhikers-builder.pages.dev.
hitchhikers-builder.pages.dev. 300 IN	A	172.66.46.211
hitchhikers-builder.pages.dev. 300 IN	A	172.66.45.45
```
