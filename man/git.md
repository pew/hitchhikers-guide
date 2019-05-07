# git

some commands I always forget

## delete branch locally and remotely

```
git push --delete <remote_name> <branch_name>
git branch -d <branch_name>
```

example:

```
git push --delete origin short_url
git branch -d short_url
```

## git submodule

too confusing.

### add git submodule

```
git submodule add https://github.com/vimwiki/vimwiki.git
```

### init git submodules

```
git submodule init
git submodule update
```

