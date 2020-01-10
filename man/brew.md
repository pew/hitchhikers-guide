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
