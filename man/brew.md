# brew / homebrew

## restore all brew packages on a new system

create a `Brewfile` ... well, on your old/original system

```
brew bundle dump --file Brewfile
```

install all packages:

```
brew bundle
```

## update brew (packages/apps)

```
brew update
brew upgrade
brew cask upgrade
```

## clear cache

because `brew cleanup` does not clean up.

```
rm -r $(brew --cache)
```

there's also:

```
brew cleanup
```

to make it even more confusing, there's also:

```shell
brew cleanup -s
```

> Scrub the cache, including downloads for even the latest versions. Note downloads for any installed formulae or casks will still not be deleted. If you want to delete those too: `rm -rf "$(brew --cache)"`

## reinstall all packages

```
brew list | xargs brew reinstall
```