---
date created: Thursday, October 18th 2018, 1:02:43 pm
date modified: Saturday, November 15th 2025, 12:00:52 pm
tags:
  - regex
  - re2
  - markdown
title: regex
---

# regex

I just can't get over it, it's too hard for me.

## match everything after match

the `libexec` part here is for macOS, you need gnu grep to do `-P`

```
/usr/local/opt/grep/libexec/gnubin/grep -oP '/repos/\K.*'
```

this will match everything after `repos/`, the `K` is important here. the `.*` says that it should match everything afterwards.

## remove blank / empty lines

```
/^[\s]*$\n/
```

to use it in editors like bbedit, use `^[\s]*$\n`

## remove blank space end of line

```
\s+$
```

## google re2 / golang(?)

match `foo.example.com` and `foo-bar.example.com`:

```
(foo|foo-bar|).example.com
```

[you can test your expression here](https://regoio.herokuapp.com).

## swap markdown heading levels

swap H1 (`#`) with H3 (`###`)

```shell
sed -E -i '' 's/^([[:space:]]*)#([[:space:]]+)(.*)$/\1###\2\3/' ./*.md
```

## remove `---` delimiters

common example when used in markdown, it looks for the delimiter with a blank line before and after:

```

---

```

```shell
sed -E -i '' '/^[[:space:]]*---[[:space:]]*$/d' ./*.md
```

## remove all `---` (HR) delimiters

```shell
sed -E -i '' '/^[[:space:]]*(---|\*\*\*|___)[[:space:]]*$/d' ./*.md
```
