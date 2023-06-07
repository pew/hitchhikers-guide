# sips

scriptable image processing system. Part of macOS.

## convert HEIC to png

**just one:**

```shell
sips -s format png image.HEIC --out image.png
```

**multiple in a loop:**

```shell
for i in *.HEIC; do sips -s format png "${i}" --out "${i%.*}.png"; done
```
