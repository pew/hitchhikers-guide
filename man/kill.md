---
date created: Saturday, July 4th 2026, 5:36:33 pm
date modified: Saturday, July 4th 2026, 5:45:38 pm
tags:
  - linux
---

# kill

kill sends a signal to one or more processes, usually to ask to terminate or force them to stop

## kill app / process by name

works also for things like `Codex.app` on macOS, since `-f` matches the whole command:

list matching processes:

```shell
pgrep -af 'Codex.app'
pgrep -fl 'Codex.app'
```

kill matching processes:

```shell
pkill -f 'Codex.app'
pkill -f '/Applications/Codex\.app/' # might be safer if it matches other apps, too
```

## terminate exact process

this matches the exact process name:

```shell
pgrep -ax codex
pgrep -xl codex
```

this ends the process:

```shell
pkill -x codex
```
