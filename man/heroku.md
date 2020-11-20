# heroku

## restore heroku postgresql database

when `heroku pg:backups:restores` just doesn't work for some reason without giving any good messages, or you get errors like these but have done the things according to the docs:

> pg_restore: error: did not find magic string in file header

> pg_restore: error: entry ID -1234 out of range -- perhaps a corrupt TOC

**restore via psql cli:**

fortunately heroku gives direct postgresql shell access. first, export your database

```shell
pg_dump --no-acl --no-owner -h localhost -U postgres postgres > dump.sql
```

then **import** the database

```shell
heroku pg:psql < dump.sql
```

