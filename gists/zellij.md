---
date created: Sunday, July 5th 2026, 3:40:18 pm
date modified: Monday, July 6th 2026, 7:55:23 am
tags:
  - zellij
  - tmux
---

# zellij

something new.

## zellij cheat sheet

### tabs

| Action | Keys |
|---|---|
| Create new tab | `Ctrl-t` then `n` |
| Next tab | `Ctrl-t` then `l` |
| Previous tab | `Ctrl-t` then `h` |
| Go to tab number | `Ctrl-t` then `1` … `9` |

### panes

Zellij calls terminal "windows" **panes**.

| Action                     | Keys                                                               |
| -------------------------- | ------------------------------------------------------------------ |
| Create new pane            | `Ctrl-p` then `n`                                                  |
| Move between panes         | `Alt-h/j/k/l`                                                      |
| Move between panes, arrows | `Alt-←/↓/↑/→`                                                      |
| Split down                 | `Ctrl-p` then `d`                                                  |
| Split right                | `Ctrl-p` then `r`                                                  |

### session

| Action          | Keys                     |
| --------------- | ------------------------ |
| attach / create | `zellij attach --create` |
| detach          | `Ctrl-o` then `d`        |
| quit zellij     | `Ctrl-q`                 |
