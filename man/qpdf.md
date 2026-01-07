---
date created: Wednesday, January 7th 2026, 9:25:04 am
date modified: Wednesday, January 7th 2026, 9:28:33 am
tags:
  - metadata
  - security
  - privacy
  - opsec
  - pdf
---

# qpdf

- project on github: [qpdf: qpdf: A content-preserving PDF document transformer](https://github.com/qpdf/qpdf)
- see also [exiftool](/man/exiftool/)

## install qpdf

```
brew install qpdf
```

## remove metadata from pdf

if in doubt, consider using [dangerzone](https://dangerzone.rocks)

```shell
qpdf --qdf --object-streams=disable input.pdf output.pdf
```

as part of an (zsh) alias:

```shell
function qpdfclean() {
  emulate -L zsh
  local f
  for f in "$@"; do
    qpdf --qdf --object-streams=disable -- "$f" "${f:r}_c.pdf"
  done
}
```
