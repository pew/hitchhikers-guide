# zsh

## share history across sessions / terminals

this used to be the default for [oh my zsh](https://ohmyz.sh) users but [they removed this feature](https://github.com/ohmyzsh/ohmyzsh/commit/23760228908d14a4644718869d5ebfb7b0dde6a7) without warning (granted, I don't know how you notify people about such a *breaking* change. nevermind...) but since this feature is just awesome, just add this to your local `~/.zshrc` file to get it back:

```shell
setopt inc_append_history     # add commands to HISTFILE in order of execution
setopt share_history          # share command history data
```

restart your shell(s) and everything's awesome again.
