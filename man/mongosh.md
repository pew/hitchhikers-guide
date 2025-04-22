---
date created: Tuesday, April 22nd 2025, 5:59:13 am
date modified: Tuesday, April 22nd 2025, 6:03:17 am
tags:
  - mongodb
---

# mongosh

manage mongodb using the command line

## mongosh

`mongosh` is the tool to work with mongodb on the CLI

```shell
mongosh
```

## list databases

```
show databases
```

## show collections

first open the database, then show the collections

```shell
use databaseName
show collections
```

## database backup

backup all databases:

```shell
kubectl exec -it --tty mongodb-foo-bar -- sh -c '/usr/bin/mongodump --compressors=zstd --archive' | zstd - -o mongodb_$(date +%F).zst
```

backup just `mydb`:

```shell
kubectl exec -it --tty mongodb-foo-bar -- sh -c '/usr/bin/mongodump --compressors=zstd --db mydb --archive' | zstd - -o mydb_mongodb_$(date +%F).zst
```
