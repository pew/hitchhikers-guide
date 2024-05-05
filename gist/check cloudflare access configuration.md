---
date created: Sunday, May 5th 2024, 12:00:17 pm
date modified: Sunday, May 5th 2024, 12:12:12 pm
tags:
  - cloudflare
---

# check cloudflare access configuration

zero trust, right? this script will iterate through all configured [Cloudflare Access](https://developers.cloudflare.com/cloudflare-one/applications/configure-apps/) domains and checks if there's either a redirect to the identity provider (IdP) in place or a 403 status code returned in case it's using service authentication.

make sure to have `jq` installed to use this script.

I'm executing this on a mac and have my Cloudflare API key stored in Keychain.app with the name `cloudflare read only api`. If you create a (read only) Cloudflare API token and save it as `cloudflare read only api` in your Keychain the script will just work, otherwise you need to adapt the `hosts=` line with your own token/keychain thing.

```shell
#!/bin/bash

access_name="example.cloudflareaccess.com" # your cloudflare zero trust team name
account_id="1234foobar" # your cloudflare account ID

hosts=$(curl -s -H "Authorization: Bearer $(/usr/bin/security find-generic-password -l "cloudflare read only api" -w)" -H "Content-Type:application/json" "https://api.cloudflare.com/client/v4/accounts/$account_id/access/apps" | jq -r '.result[].self_hosted_domains | .[]?')
for host in $hosts; do
  echo -en "checking \033[1m$host\033[0m: "

  response=$(curl -sSI -X GET -o /dev/null -w "%{http_code} %{redirect_url}" "https://$host/")
  status_code=$(echo "$response" | awk '{print $1}')
  redirect_url=$(echo "$response" | awk '{print $2}')

  if [ "$status_code" = "403" ]; then
    echo -e "status code: \033[1m$status_code\033[0m ✅"
  elif [ -n "$redirect_url" ]; then
      if [[ "$redirect_url" == https://"$access_name"/* ]]; then
          echo "redirected to IdP ✅"
      else
          echo "❌"
      fi
  else
      echo -e "status code: \033[1m$status_code\033[0m NO redirect ❌❌❌"
  fi
done
```
