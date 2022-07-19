# update-alternatives

## set editor (non interactive)

set vim as the default editor (and for `vi`):

```shell
update-alternatives --install /usr/bin/editor editor /usr/bin/vim 1
update-alternatives --set editor /usr/bin/vim
update-alternatives --install /usr/bin/vi vi /usr/bin/vim 1
update-alternatives --set vi /usr/bin/vim
```

[thanks](https://askubuntu.com/questions/891928/how-can-i-add-my-desired-editor-to-the-update-alternatives-interactive-menu)
