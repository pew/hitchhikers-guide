---
date created: Monday, February 2nd 2026, 7:58:13 am
date modified: Sunday, March 1st 2026, 11:24:32 am
tags:
  - pandoc
---

# pandoc

convert all the (text) things, [check out pandoc](https://pandoc.org/)

## convert markdown to html

```shell
pandoc README.md -o README.html
```

## convert html to markdown

```shell
pandoc README.html -o README.md
```

## convert anything to markdown

also extract attachments

```shell
pandoc input.epub -t gfm --extract-media=./images -o output.md
```

## drop html tags which cannot be converted (to markdown)

```shell
pandoc input.epub -t gfm-raw_html --extract-media=./images -o output.md
```
