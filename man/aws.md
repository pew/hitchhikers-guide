---
date created: Friday, June 9th 2023, 11:30:38 am
date modified: Tuesday, December 31st 2024, 10:58:30 am
tags:
  - aws
---

# aws

some aws cli commands I'll probably forget about since I'm only using them once in a while

## fix pager view / output / annoyances

what the fork...? see [this pull request](https://github.com/aws/aws-cli/pull/4702#issue-344978525), do one of these things:

* add `cli_pager = cat` to `~/.aws/config` AND maybe even in `~/.aws/credentials` if you're using multiple profiles. somehow it doesn't work in the config file for me
* set the env var `AWS_PAGER=""`

## s3

### recursively copy files starting with a prefix

download only files starting with `2023`

```shell
aws s3 cp s3://your-bucket-name/ ~/Downloads/ --recursive --exclude "*" --include "2023*"
```

### sort `aws s3 ls`  by date

```shell
aws s3 ls s3://foobar/ --recursive | sort -k1,1 -k2,2
```
