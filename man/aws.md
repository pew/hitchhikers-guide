# aws (aws-cli)

some aws cli commands I'll probably forget about since I'm only using them once in a while

## aws ssm

get something out of ssm:

```
aws ssm get-parameter --name DOCKER_ENV --query Parameter.Value --output text > test.env
```

put something in there (also, overwrite existing):

```
aws ssm put-parameter --overwrite --name DOCKER_ENV --type String --value "$(cat test.env)"
```

