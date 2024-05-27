---
tags: 
  - regex
  - re2
title: regex
date created: Thursday, October 18th 2018, 1:02:43 pm
date modified: Sunday, July 31st 2022, 10:25:23 am
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
