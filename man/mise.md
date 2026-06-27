---
date created: Friday, May 29th 2026, 8:55:43 am
date modified: Saturday, June 27th 2026, 2:53:40 pm
tags:
  - mise
  - npm
  - python
  - node
---

# mise

## add packages

**globally:**

```
mise use -g uv@latest
```

**project scope:**

```
mise use uv@latest
```

### add npm packages

```shell
mise use -g npm:@openai/codex
mise use -g npm:skills
```

## upgrade packages

```
mise upgrade
```

upgrade to the latest available version:

```shell
mise upgrade --bump
```

## cleanup old packages

```
mise prune
```

## cleanup mise cache

```shell
mise cache clear
```
