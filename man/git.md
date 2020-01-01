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

## git submodules

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

## delete file / folder from history

well, things happen from time to time. I just wanted to get rid of a folder and move it to git *lfs*


```
git filter-branch -f --index-filter "git rm -rf --cached --ignore-unmatch .assets" -- --all
```

also cleanup remote:

```
rm -rf .git/refs/original/
git reflog expire --expire=now --all
git gc --aggressive --prune=now
git push --all --force
```

[source](https://stackoverflow.com/a/24526351)
