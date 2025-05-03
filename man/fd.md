---
date created: Saturday, July 10th 2021, 9:55:50 am
date modified: Saturday, May 3rd 2025, 10:29:38 am
tags: 
---

# fd

- [A simple, fast and user-friendly alternative to 'find'](https://github.com/sharkdp/fd)

cool alternative to [find](/man/find), ignores things like `.git` and `node_modules` etc.

## format output

use with `--format`, for example: `--format {/}` to only return the filename

| Placeholder | Expands to                |
| ----------- | ------------------------- |
| `{}`        | full path                 |
| `{.}`       | full path minus extension |
| `{/}`       | basename                  |
| `{/.}`      | basename minus extension  |
| `{//}`      | parent directory          |

## find exact match

let's say I want to search for `curl` in a folder, but not for `curl.rb`

```
fd -g curl /opt/homebrew
```

this might not yield any results, so combine it with `-u` to ignore the *smart* ignore list (the cool feature about `fd`... yes):

```
fd -gu curl /opt/homebrew
```

## ignore ignore list

ignore the ignore list to find things, ~~major major major major.~~ aka *unrestricted* mode

```
fd -u <pattern> /your/path
```

## include hidden files

```
fd -uu <pattern> /your/path
```

## find all dotfiles in your home directory

```shell
fd --hidden --max-depth 1 --follow --type file '^\.' ~
fd --hidden --max-depth 1 --follow --type file --format '{/}' '^\.' ~ # just show the filename
```
