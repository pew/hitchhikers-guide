---
date created: Saturday, November 22nd 2025, 11:48:22 am
date modified: Saturday, November 22nd 2025, 11:49:42 am
tags:
  - svg
  - png
---

# rsvg-convert

## install rsvg-convert

```shell
brew install librsvg
```

## convert svg to png 1:1

```shell
rsvg-convert icon.svg -o icon.png
```

## convert svg to png with explicit size

```shell
rsvg-convert icon.svg -o icon.png -w 512 -h 512
```
