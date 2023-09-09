---
date created: Saturday, September 9th 2023, 11:00:17 am
date modified: Saturday, September 9th 2023, 11:04:48 am
tags:
  - s3
  - garage
---

# garage (s3)

[garage](https://garagehq.deuxfleurs.fr) is an S3 API compatible object storage server which can be self-hosted, similar to [minio](https://min.io).

see also [self-hosted s3 compatible storage](self-hosted%20s3%20compatible%20storage.md)

## getting started

The docs are quite good, [here's an example](https://garagehq.deuxfleurs.fr/documentation/cookbook/real-world/) how to get started using docker (compose).

## create buckets

Assuming you deployed garage with docker using compose. The following will create a bucket, generate a access/secret key for this bucket and grants read, write, owner permissions to the key pair.

```shell
BUCKET_NAME=incoming
docker compose exec garage /garage bucket create $BUCKET_NAME
docker compose exec garage /garage key new --name $BUCKET_NAME
docker compose exec garage /garage bucket allow --read --write --owner $BUCKET_NAME --key $BUCKET_NAME
```
