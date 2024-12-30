---
date created: Friday, December 27th 2024, 4:34:01 pm
date modified: Monday, December 30th 2024, 10:25:14 am
tags: 
---

# playbook - ubuntu dist-upgrade

upgrading ubuntu and managing configuration file changes, you might also want to use tools such as [etckeeper](https://etckeeper.branchable.com/)

## upgrade using `do-release-upgrade`

```shell
DEBIAN_FRONTEND=noninteractive do-release-upgrade --frontend=DistUpgradeViewNonInteractive
```

## post-upgrade: manage configuration file changes

### locate all changed configuration files

- **for `.dpkg-*` files:**

```shell
find /etc -name "*.dpkg-*"
```

- **for `.ucf-dist` files:**

```shell
find /etc -name "*.ucf-dist"
```

- **for `.distUpgrade` files:**

```shell
find /etc -name "*.distUpgrade*"
```

### compare and merge changes

- use `vimdiff` or a similar tool to compare the original file with the new version:

```shell
vimdiff /path/to/config.file /path/to/config.file.dpkg-dist
vimdiff /path/to/config.file /path/to/config.file.ucf-dist
```

### remove temporary files

- once resolved, delete `.dpkg-*` and `.ucf-dist` files:

```shell
rm /path/to/config.file.dpkg-dist
rm /path/to/config.file.ucf-dist
```
