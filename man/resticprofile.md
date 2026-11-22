---
date created: Sunday, December 7th 2025, 11:43:39 am
date modified: Sunday, November 22nd 2026, 8:40:26 am
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
resticprofile # uses the default profile
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

## prune and forget snapshots

use **`forget` to delete old snapshots** and **`prune` to reclaim storage from unreferenced data**.

**preview a retention policy**, for example keeping the latest 10 snapshots:

```bash
resticprofile --name default forget --keep-last 10 --prune --dry-run
```

**apply the reviewed policy:**

```bash
resticprofile --name default forget --keep-last 10 --prune
```

**clean up unreferenced data**, without deleting additional snapshots:

```bash
resticprofile --name default prune --dry-run
resticprofile --name default prune
```

delete a **specific snapshot**, use its ID:

```bash
resticprofile --name default forget SNAPSHOT_ID --prune --dry-run
# Remove --dry-run after reviewing the result.
```
