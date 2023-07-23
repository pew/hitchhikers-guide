---
date created: Thursday, November 19th 2020, 5:03:03 am
date modified: Sunday, July 23rd 2023, 10:19:17 am
tags:
  - icloud
  - brctl
  - bird
---

# brctl

or... how to work with iCloud drive hiccups. to just go ahead, run

```shell
brctl
```

and check the available commands

## monitor iCloud drive sync status

`com.apple.CloudDocs` refers to iCloud Drive

```shell
brctl monitor com.apple.CloudDocs
```

the thing is, I have no idea how to fix the issues reported in there. it'll tell you which things are not able to sync across icloud and there's just no way to fix things. go back to dropbox if you want something reliable.

## download all iCloud drive files

2021, you still can't trust iCloud to have all files downloaded manually. If you really want to make sure that all files are locally, switch to another syncing tool like Dropbox.

otherwise, this might work:

```shell
cd ~/Library/Mobile\ Documents/com~apple~CloudDocs/ && find . -type f -print0 | xargs -0 brctl download
```

## restart iCloud process

```shell
killall bird
```

## debug iCloud with Cirrus

- [Cirrus is a free utility to help with iCloud issues](https://eclecticlight.co/cirrus-bailiff/). iCloud Drive, CloudDocs, all iCloud related things. It also let's you download and evict files from iCloud instead of using the command line like described above.
