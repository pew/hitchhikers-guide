---
date created: Friday, February 25th 2022, 5:36:33 am
date modified: Saturday, October 26th 2024, 11:04:36 am
tags: 
---

# gh - github cli

## install github-cli

- [see how to get and install github cli](https://cli.github.com)

```shell
brew install gh
```

## list all starred repos

```shell
GH_PAGER="" gh api user/starred --paginate --jq '.[].full_name'
```

## removed starred repo

turns out, you can't unstar a repo on the web which was taken down by a DMCA request

```
gh api -X DELETE user/starred/username/repo
```
