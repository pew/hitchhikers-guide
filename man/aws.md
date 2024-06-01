---
date created: Friday, June 9th 2023, 11:30:38 am
date modified: Monday, May 20th 2024, 10:28:01 am
tags:
  - aws
---

# aws

## aws cli v2

some aws cli commands I'll probably forget about since I'm only using them once in a while

### fix pager view / output / annoyances

what the fork...? see [this pull request](https://github.com/aws/aws-cli/pull/4702#issue-344978525), do one of these things:

* add `cli_pager = cat` to `~/.aws/config` AND maybe even in `~/.aws/credentials` if you're using multiple profiles. somehow it doesn't work in the config file for me
* set the env var `AWS_PAGER=""`

### recursively copy files starting with a prefix

download only files starting with `2023`

```shell
aws s3 cp s3://your-bucket-name/ ~/Downloads/ --recursive --exclude "*" --include "2023*"
```

## aws (aws-cli) v1

might work with v2, might not. don't know.

### aws ssm

get something out of ssm:

```
aws ssm get-parameter --name DOCKER_ENV --query Parameter.Value --output text > test.env
```

put something in there (also, overwrite existing):

```
aws ssm put-parameter --overwrite --name DOCKER_ENV --type String --value "$(cat test.env)"
```
