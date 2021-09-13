# brctl

or... how to work with icloud drive hiccups. to just go ahead, run

```shell
brctl
```

and check the available commands

## monitor icloud drive sync status

`com.apple.CloudDocs` refers to iCloud Drive

```shell
brctl monitor com.apple.CloudDocs
```

the thing is, I have no idea how to fix the issues reported in there. it'll tell you which things are not able to sync across icloud and there's just no way to fix things. go back to dropbox if you want something reliable.

## download all iCloud drive files

2021, you still can't trust iCloud to have all files downloaded manually. If you really want to make sure that all files are locally, switch to another syncing tool like Dropbox.

otherwise, this might work:

```
cd ~/Library/Mobile\ Documents/com~apple~CloudDocs/
fd . | while read file; do brctl download "$file";done
```
