---
date created: Monday, September 29th 2025, 10:11:50 am
date modified: Monday, September 29th 2025, 10:15:54 am
tags:
  - postgres
  - psql
---

# psql

some psql / postgres commands you probably need every now and then

## dump database

```shell
pg_dumpall -U atuin > atuin_$(date +%F).sql
```

## restore database

```shell
cat atuin_2025-09-29.sql | psql -U atuin
```

## docker: dump database

```shell
docker exec -it atuin-postgresql-1 pg_dumpall -U atuin > atuin_$(date +%F).sql
```

## docker: restore database

if you're upgrading and the databases aren't too large and a bit of downtime is ok:

```shell
docker compose down atuin # stop services
docker volume rm atuin_database # delete postgres volume
docker compose up -d postgresql # start just postgres
cat atuin_2025-09-29.sql | docker exec -i atuin-postgresql-1 psql -U atuin
```
