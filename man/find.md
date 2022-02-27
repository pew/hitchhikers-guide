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

## find 0 byte files

… you may want to double check if you actually want to delete them, but I had some conflicts in syncthing and checked for them manually

```
find /data -size 0
```