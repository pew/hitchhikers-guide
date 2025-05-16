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
