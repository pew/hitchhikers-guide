---
date created: Saturday, October 3rd 2026, 9:34:19 am
date modified: Saturday, October 3rd 2026, 9:38:20 am
tags:
  - linux
  - ssh
  - clipboard
---

# copy to local clipboard

I'm used to piping things into my local macOS clipboard using ` | pbcopy` all day long, here's a way to get the same results when connected to a remote system via ssh.

just add this as a function into your dotfiles, like `.zshrc`, or `.zsh_aliases`, or `.bashrc` etc.:

```shell
pbcopy() {
  printf '\e]52;c;%s\a' "$(base64 | tr -d '\n')"
}
```

I'm managing my dotfiles using [chezmoi](https://chezmoi.io/) and have a template so the above function will only be applied to linux hosts, that's why I picked the same name as I'm already familiar with from macOS.
