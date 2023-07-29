---
date created: Saturday, July 29th 2023, 10:33:37 am
date modified: Saturday, July 29th 2023, 10:39:27 am
tags:
  - cloudflare
  - cloudflared
  - cloudflare_tunnel
---

# install latest `cloudflared` package

- download and install the latest `cloudflared` debian package and restart the service
- using `dpkg --print-architecture` it should pick the right version for the running OS

```shell
curl -L -o cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-$(dpkg --print-architecture).deb && dpkg -i cloudflared.deb && systemctl restart cloudflared
```
