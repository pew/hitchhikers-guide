---
date created: Sunday, December 7th 2025, 11:43:39 am
date modified: Sunday, December 7th 2025, 11:48:39 am
tags:
  - restic
  - backup
---

# resticprofile

- see also [restic](/man/restic/)
- you can always add the argument `--name <profile_name>` to select a specific profile, `default` is standard

## list profiles

```shell
resticprofile profiles
```

## list snapshots

```shell
resticprofile --name default snapshots
```

## list items in snapshot

- `latest` is a special snapshot name, referring to the latest snapshot

```shell
resticprofile ls latest
```

## mount backup

```shell
resticprofile mount /restic_restore
```

- you can then browse the contents, for the latest snapshot for example:

```shell
ls /restic_restore/snapshots/latest/
```
