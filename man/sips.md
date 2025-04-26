# sips

scriptable image processing system. Part of macOS.

## convert heic to png or jpg

**just one:**

```shell
sips -s format png image.heic --out image.png
sips -s format jpeg image.heic --out image.jpg
```

**multiple in a loop:**

```shell
for i in *.heic; do sips -s format png "${i}" --out "${i%.*}.png"; done
for i in *.heic; do sips -s format jpeg "${i}" --out "${i%.heic}.jpg"; done
```
