---
date created: Sunday, January 19th 2025, 2:27:53 pm
date modified: Sunday, January 19th 2025, 2:30:30 pm
tags:
  - filesystem
---

# fatrace

fatrace - report system wide file access events

## monitor filesystem access by process name

figure out why your hard drives are waking up at seemingly random times.

**just monitor the current mount point**

to only monitor filesystem access in the mounted path `/mnt`, change into that directory and use the `-c` flag. `-t` adds a timestamp and `-o` writes everything out to a file

```shell
cd /mnt
fatrace -c -t -o /tmp/fatrace.log
```
