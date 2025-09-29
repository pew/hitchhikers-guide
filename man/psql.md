---
date created: Monday, September 29th 2025, 10:11:50 am
date modified: Monday, September 29th 2025, 10:44:11 am
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

## k8s / kubernetes: dump database

**single pod/container export:**

```shell
kubectl exec pod/<postgres-pod> -- pg_dumpall -U miniflux > miniflux.sql
```

**multi pod/container export:**

```shell
kubectl exec pod/miniflux-xxx-xxx -c db -- pg_dumpall -U miniflux > miniflux.sql
```

## k8s / kubernetes: restore database

**single pod/container import:**

```shell
kubectl exec -i pod/<postgres-pod> -- psql -U miniflux < miniflux.sql
```

**multi-pod import:**

if you have a deployment / pod with multiple containers, patch the **non-database** containers to execute the sleep command so you can export the database properly:

```shell
kubectl patch deploy/miniflux -p '{
  "spec":{"template":{"spec":{
    "containers":[{"name":"miniflux","command":["sleep","infinity"]}]
  }}}
}'
```

when the database has been restored, revert the patch:

```shell
kubectl rollout undo deploy/miniflux
```

and restore:

```shell
kubectl exec -i pod/miniflux-xxx-xxx -c db -- psql -U miniflux < miniflux.sql
```
