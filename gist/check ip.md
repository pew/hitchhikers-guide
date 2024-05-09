---
date created: Thursday, May 9th 2024, 11:32:56 am
date modified: Thursday, May 9th 2024, 11:41:53 am
tags:
  - ip
---

# check ip

what's my IP?

## check via DNS

**Cloudflare**

```shell
dig -4 @1.1.1.1 +short txt ch whoami.cloudflare
dig -6 @2606:4700:4700::1111 +short txt ch whoami.cloudflare
dig @john.ns.cloudflare.com +short ch txt id.server
```

**Google**

```shell
dig -4 @ns1.google.com TXT +short o-o.myaddr.l.google.com
dig -6 @ns1.google.com TXT +short o-o.myaddr.l.google.com
```

**OpenDNS**

```shell
dig -4 +short ANY @resolver1.opendns.com myip.opendns.com
dig -6 +short ANY @resolver1.opendns.com myip.opendns.com
```
