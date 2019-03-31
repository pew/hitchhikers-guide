# find

## find incomplete / dead rsync transfers

find them:

```
find /mnt/media/ -type f -iname ".*.*.??????" -ls
```

delete them:

```
find /mnt/media/ -type f -iname ".*.*.??????" -delete
```
