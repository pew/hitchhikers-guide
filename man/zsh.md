# zsh

## share history across sessions / terminals

this used to be the default for [oh my zsh](https://ohmyz.sh) users but [they removed this feature](https://github.com/ohmyzsh/ohmyzsh/commit/23760228908d14a4644718869d5ebfb7b0dde6a7) without warning (granted, I don't know how you notify people about such a *breaking* change. nevermind...) but since this feature is just awesome, just add this to your local `~/.zshrc` file to get it back:

```shell
setopt inc_append_history     # add commands to HISTFILE in order of execution
setopt share_history          # share command history data
```

restart your shell(s) and everything's awesome again.

## ignore history with beginning space

say you want to prevent adding a command into the zsh history because it contains an API key, you can do this by putting a space in front of the command, like so (note the leading space):

```
 super_secret-api_key
```

to enable this with zsh, either add the following to your `~/.zshrc` file or execute it manually beforehand:

```
setopt HIST_IGNORE_SPACE
```

## (oh-my-zsh) fix *no match found*

add this to your `~/.zshrc`:

```
unsetopt nomatch
```

## don't add backslashes

[some more about that here](https://ilayk.com/2021/07/23/fix-oh-my-zsh-&-iterm-copy-paste-backslashes)