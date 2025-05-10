---
date created: Saturday, May 10th 2025, 10:06:56 am
date modified: Saturday, May 10th 2025, 10:10:52 am
tags:
  - password
---

# bitwarden-cli

work with your [bitwarden](https://bitwarden.com/) vault from the command line.

## installation

```shell
brew install bitwarden-cli
```

## use in scripts

to use bitwarden-cli in scripts, you can pass `--raw` to the unlock command and retrieve only the session token:

```shell
BW_SESSION=$(bw unlock --raw)
export BW_SESSION
```

## unlock / lock

```shell
bw unlock
bw lock
```

## search

you can also pass `| jq` to it since the output is in json

```shell
bw list items --search "dnscontrol"
```

## get username / password

use the search from above, and take the `id` to  get the username/password:

```shell
bw get username "foo-bar-random-id"
bw get password "foo-bar-random-id"
```
