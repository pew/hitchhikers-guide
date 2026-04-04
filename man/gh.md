---
date created: Friday, February 25th 2022, 5:36:33 am
date modified: Saturday, April 4th 2026, 10:18:19 am
tags:
  - git
  - github
---

# gh - github cli

## install github-cli

- [see how to get and install github cli](https://cli.github.com)

```shell
brew install gh
```

## configure options

the config is stored in `~/.config/gh/config.yml`

### set pager

```shell
gh config set pager cat
```

### configure editor

```
gh config set editor "code --wait"
```

## github stars

### list all starred repos

```shell
GH_PAGER="" gh api user/starred --paginate --jq '.[].full_name'
```

### removed starred repo

turns out, you can't unstar a repo on the web which was taken down by a DMCA request

```
gh api -X DELETE user/starred/username/repo
```

## manage pull requests

### list pull requests

```shell
gh pr list
```

### (squash) merge and delete remote branch

replace `23` with your pr id

```shell
gh pr merge 23 --auto -s -d
```

### close without merging and delete remote branch

replace `42` with your pr id

```shell
gh pr close 42 -d
```

## list repositories without a description

list all your own repos which are not archived and are missing a description

```shell
gh repo list --source --no-archived -L 1000 \
  --json nameWithOwner,description \
  --jq '.[] | select((.description == null) or (.description == "")) | .nameWithOwner'
```
