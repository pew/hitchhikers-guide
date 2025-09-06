---
date created: Saturday, September 6th 2025, 10:39:45 am
date modified: Saturday, September 6th 2025, 10:44:23 am
tags:
  - docker
  - container
---

# skopeo

[skopeo: Work with remote images registries - retrieving information, images, signing content](https://github.com/containers/skopeo/)

## configure container registry

it uses the docker hub by default when you just use `docker://`, otherwise specify the path like so: `docker://quay.io/`

## list docker hub image tags

life is too short to try and find anything on the docker hub website when it comes to image tags…

```shell
skopeo list-tags --override-os linux docker://grafana/loki
skopeo list-tags --override-os linux docker://grafana/loki | jq '.Tags'
```

## inspect images

when run from macos, it might be easier to just override the OS if you want to get some specific information:

```shell
skopeo inspect --override-os linux docker://grafana/loki
```
