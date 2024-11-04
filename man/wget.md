---
date created: Saturday, April 6th 2024, 6:14:59 am
date modified: Monday, November 4th 2024, 6:03:37 am
tags: 
---

# wget

## set filename automatically

use `--content-disposition` for that. [source]([url](https://superuser.com/a/301051))

```shell
wget --content-disposition https://example.com
```

## download only pdf / specific file types from site

```shell
wget -r -A pdf https://example.com/
```

## skip if file exist already

```shell
wget -nc
```

## bind to source ip address (network interface)

```shell
wget --bind-address 10.0.0.5
```
