---
tags:
  - cloudflare
  - zero_trust
---

# cloudflare - list zero trust ipv4 & ipv6 assignments

**requirements:**

```shell
pip install requests
```

**code:**

```python
import json
import requests

account_id = "abcfoo"
api_key = "f00bar"

headers = {
    "Authorization": "Bearer {}".format(api_key),
    "content-type": "application/json",
}


def get_devices():
    devices = requests.get(
        "https://api.cloudflare.com/client/v4/accounts/{}/devices".format(account_id),
        headers=headers,
    )
    data = devices.json()

    return data["result"]


def get_ip_addresses(devices):
    out = []
    for device in devices:
        device_id = device["id"]
        device_name = device["name"]

        device_info = requests.get(
            "https://api.cloudflare.com/client/v4/accounts/{}/devices/{}/ip".format(
                account_id, device_id
            ),
            headers=headers,
        )
        output = device_info.json()
        device_ipv4 = output["result"]["result"]["ipv4"]
        device_ipv6 = output["result"]["result"]["ipv6"]

        out.append(
            {
                "id": device_id,
                "name": device_name,
                "ipv4": device_ipv4,
                "ipv6": device_ipv6,
            }
        )
    return out


if __name__ == "__main__":
    devices = get_devices()
    ip_addresses = get_ip_addresses(devices)
    print(json.dumps(ip_addresses, indent=2))
```
