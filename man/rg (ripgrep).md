---
date created: Friday, January 2nd 2026, 10:27:37 am
date modified: Friday, January 2nd 2026, 10:33:19 am
tags:
  - grep
  - rg
---

# rg (ripgrep)

- [GitHub - ripgrep recursively searches directories for a regex pattern while respecting your gitignore](https://github.com/BurntSushi/ripgrep)

## list filename(s) only

checks the contents of the folders/files, but only returns the matching filename(s):

```shell
rg -l <your search pattern>
```

## search in ignored and hidden files

`rg` skips over files in some hidden folders and looks at ignore definitions such as `.gitignore`, to force `rg` to search everywhere:

```shell
rg --no-ignore --hidden <your pattern>
```

to ignore all filters, use:

```shell
rg -uuu
```
