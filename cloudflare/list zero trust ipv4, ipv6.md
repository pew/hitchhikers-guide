---
date created: Friday, June 23rd 2023, 5:47:44 am
date modified: Wednesday, September 6th 2023, 12:03:09 pm
tags:
  - cloudflare
  - zero_trust
---

# list zero trust ipv4 & ipv6 assignments

```python
# add your account id below
# add a (zero trust read only) api token below

import urllib.request
import json

account_id = "foo"
api_key = "f00bar"

headers = {
    "Authorization": "Bearer {}".format(api_key),
    "content-type": "application/json",
}


def get_devices():
    list_complete = False
    cursor = ""
    devices = []

    while list_complete == False:
        req = urllib.request.Request(
            "https://api.cloudflare.com/client/v4/accounts/{}/devices".format(
                account_id
            )
            + ("" if cursor is None else "?cursor={}".format(cursor)),
            headers=headers,
        )

        with urllib.request.urlopen(req) as response:
            data = json.loads(response.read().decode())

        cursor = data["result_info"]["cursor"]

        if cursor == data["result_info"]["cursor"]:
            list_complete = True
        devices.append(data["result"])

    return [item for sublist in devices for item in sublist]


def get_ip_addresses(devices):
    out = []
    for device in devices:
        device_id = device["id"]
        device_name = device["name"]

        req = urllib.request.Request(
            "https://api.cloudflare.com/client/v4/accounts/{}/devices/{}/ip".format(
                account_id, device_id
            ),
            headers=headers,
        )

        try:
            with urllib.request.urlopen(req) as response:
                output = json.loads(response.read().decode())
        except urllib.error.HTTPError as e:
            print(
                "HTTPError: {}, {} accessing ID {}".format(e.code, e.reason, device_id)
            )

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
