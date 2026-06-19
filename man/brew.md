---
date created: Monday, February 2nd 2026, 7:58:13 am
date modified: Friday, June 19th 2026, 7:32:36 am
tags: 
---

# brew / homebrew

## restore all brew packages on a new system

create a `Brewfile` ... well, on your old/original system

```shell
brew bundle dump --file Brewfile
```

install all packages:

```shell
brew bundle
```

## remove casks including associated files

warning from the man page: *May remove files which are shared between applications.*

```shell
brew uninstall --zap microsoft-edge
brew uninstall --zap --force microsoft-edge # if it has been manually deleted from /Applications/ already
```

## update brew (packages/apps)

```shell
brew update
brew upgrade
brew cask upgrade
```

## skip homebrew cask (version 6.0) upgrade

```
export HOMEBREW_NO_UPGRADE_AUTO_UPDATES_CASKS=true
```

[see also this github issue/pr](https://github.com/Homebrew/brew/pull/21985)

## clear cache

because `brew cleanup` does not clean up all the things.

```shell
brew cleanup --prune=all -s
rm -r $(brew --cache)
```

## reinstall all packages

```shell
brew list | xargs brew reinstall
```
