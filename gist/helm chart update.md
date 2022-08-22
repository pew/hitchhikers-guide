---
tags: 
date created: Monday, May 9th 2022, 4:05:27 am
date modified: Monday, May 9th 2022, 4:06:10 am
title: helm chart update
---

# helm chart update

```shell
helm repo update # update helm repo
helm list -n minio # show current installed version of minio
helm search repo minio # search current published version of minio in repo
helm upgrade --dry-run --install --version 4.0.1 -n minio -f minio_values.yaml minio minio/minio # dry run with the app version
helm upgrade --install --version 4.0.1 -n minio -f minio_values.yaml minio minio/minio # actual update
```
