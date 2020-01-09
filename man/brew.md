# brew / homebrew

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
