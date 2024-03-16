---
date created: Saturday, March 16th 2024, 12:05:24 pm
date modified: Saturday, March 16th 2024, 12:16:24 pm
tags: 
---

# mc (minio client)

command line tool for [MinIO](https://min.io) and basically any s3 api compatible storage

## add server configuration

replace `local` with the name of your config (any name you want), the endpoint url, access and secret key

```shell
mc config host add local http://localhost:9000 <access key> <secret access key>
```
