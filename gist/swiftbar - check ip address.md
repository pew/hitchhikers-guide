---
date created: Sunday, May 21st 2023, 9:36:01 am
date modified: Sunday, May 21st 2023, 9:43:30 am
tags:
  - macos
  - swiftbar
---

# swiftbar - check ip address

[swiftbar](https://github.com/swiftbar/SwiftBar) is a simple utility to put information in the macOS menu bar. For no particular reason, I created this little script which checks my current IPv4 and IPv6 address and displays either a lock if they both resolve to *GB*, or a warning emoji if not.

use the following filename to run the script every 10 minutes:

```shell
ipcheck.10m.sh
```

```shell
#!/usr/bin/env bash

# <bitbar.title>IP Addresses</bitbar.title>
# <bitbar.version>v1.0</bitbar.version>
# <bitbar.author>Jonas</bitbar.author>
# <bitbar.author.github>pew</bitbar.author.github>
# <bitbar.desc>Checks the client's IPv4 and IPv6 Address.</bitbar.desc>

ipv4=$(/usr/bin/curl -s -4 https://ipv4.clumsy.dev/headers?name=cf-ipcountry)
ipv6=$(/usr/bin/curl -s -6 https://ipv6.clumsy.dev/headers?name=cf-ipcountry)

# Check if both variables are "GB"
if [[ "$ipv4" == "GB" && "$ipv6" == "GB" ]]; then
    echo ":lock.fill: | sfsize=16"
else
    # If not, echo an alert emoji
    echo "⚠️"
fi
```
