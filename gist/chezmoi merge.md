---
date created: Saturday, May 30th 2026, 9:43:34 am
date modified: Saturday, May 30th 2026, 9:49:14 am
tags:
  - chezmoi
---

# chezmoi merge

the [three-way merge in chezmoi](https://www.chezmoi.io/reference/commands/merge/) always confuses me, so here's my hope that writing it down will help my future self.

assumption: you changed `~/.config/zed/settings.json` directly and `chezmoi status` now shows that `~/.config/zed/settings.json` has been modified and you want to merge that back into chezmoi.

**start the merge flow:**

```shell
chezmoi merge ~/.config/zed/settings.json
```

by default this opens in vimdiff in three panes:

```
LEFT                         MIDDLE                                  RIGHT
Destination                  Source                                  Target
~/.config/zed/settings.json  dot_config/zed/private_settings.json    temp rendered file
current real file            chezmoi repo file                       what chezmoi would apply now
```

we want to put the change(s) into the **middle pane**, with vim you can do it like so:

```
Ctrl-w l     " move from left pane to middle pane
:diffget 1   " copy the differing hunk from pane/buffer 1, the left destination, into the middle source
:w           " save the middle source file
:qa!         " quit all panes
```

done!
