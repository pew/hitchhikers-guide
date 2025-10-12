---
date created: Sunday, October 12th 2025, 12:02:25 pm
date modified: Sunday, October 12th 2025, 12:04:34 pm
tags:
  - cloudflare
  - fritzbox
---

# cloudflare tunnel (cloudflared) + fritzbox

to avoid issues accessing the Fritz!Box web interface through Cloudflare Tunnel (cloudflared), update your tunnel config with the following:

- set http host header either to the IP of your fritzbox such as `192.168.178.1` or `fritz.box` (or whatever custom config you might have)
- Set **Disable Chunked Encoding** to **On**
