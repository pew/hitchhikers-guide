---
date created: Wednesday, April 24th 2019, 7:07:34 pm
date modified: Sunday, December 7th 2025, 11:44:10 am
tags:
  - restic
  - backup
---

# restic

- see also [resticprofile](/man/resticprofile/)

my favorite backup tool on linux, you can back up your stuff encrypted to various endpoints like amazon s3, backblaze b2, sftp and others. using rclone even to tons more. I'm not listing any more of them here since it's under active development, [check the docs out](https://restic.readthedocs.io/en/latest/)

## list snapshots

list all the snapshots available in a given *repo*:

```
restic -r restic-repo-name snapshots
```

## restore from a snapshot / backup

the most important thing you're probably not doing:

1. get the snapshot ID from the above output

```
restic -r restic-repo-name restore asdf1234 --target /tmp/restore
```

where `asdf1234` is the exact snapshot name, if you want the latest snapshot you can just use `latest` instead of the ID

**restore just a single file or folder**:

this will restore `/home/jonas` from the snapshot to `/tmp/restore`

```
restic -r restic-repo-name restore asdf1234 --target /tmp/restore --include /home/jonas/
```

## mount a snapshot

for the lazy guys, you can just mount a snapshot to restore files and folders and go through them:

```
restic -r restic-repo-name mount /mnt/restic
```

## unlock a locked repository

if you get this, because a backup failed or you hit some api limits with b2:

```
Fatal: unable to create lock in backend: repository is already locked exclusively by PID
```

do this to unlock the repository (be sure that no process is running, check the mentioned PID in the message):

```shell
restic unlock -r b2:repo-name
```

that's an example for b2 with the repo name `repo-name`
