# fd

- [A simple, fast and user-friendly alternative to 'find'](https://github.com/sharkdp/fd)

cool alternative to [find](/man/find.md), ignores things like `.git` and `node_modules` etc.

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
