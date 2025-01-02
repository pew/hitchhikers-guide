---
date created: Friday, December 27th 2024, 4:34:01 pm
date modified: Thursday, January 2nd 2025, 10:38:19 am
tags: 
---

# runbook - ubuntu dist-upgrade

upgrading ubuntu and managing configuration file changes, you might also want to use tools such as [etckeeper](https://etckeeper.branchable.com/)

## upgrade using `do-release-upgrade`

```shell
DEBIAN_FRONTEND=noninteractive do-release-upgrade --frontend=DistUpgradeViewNonInteractive
```

for a truly silent or unattended upgrade, you need to configure `dpkg` to handle changes in configuration files between versions:

```shell
sh -c 'cat > /etc/apt/apt.conf.d/90force-conf <<EOF
Dpkg::Options {
    "--force-confdef";
    "--force-confold";
}
EOF'
```

explanation from the [dpkg man page](https://manpages.debian.org/buster/dpkg/dpkg.1#OPTIONS):

```
confold: If a conffile has been modified and the version in the package did change, always keep the old version without prompting, unless the --force-confdef is also specified, in which case the default action is preferred.

confdef: If a conffile has been modified and the version in the package did change, always choose the default action without prompting. If there is no default action it will stop to ask the user unless --force-confnew or --force-confold is also been given, in which case it will use that to decide the final action.
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
