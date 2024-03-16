---
date created: Monday, August 2nd 2021, 5:48:23 am
date modified: Saturday, March 16th 2024, 12:16:48 pm
tags: 
---

# kubectl

see also [kubernetes](/man/kubernetes/)

## download kubectl for arm architecture, like an raspberry pi

I don't know why they make it so hard, but here you go:

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm/kubectl"
```

## execute command in pod

one-off command:

```shell
kubectl exec rabbitmq-0 -- rabbitmqctl list_queues
```

run with tty interactively:

```shell
kubectl exec -it --tty rabbitmq-0 -- /bin/sh
```

## get kubernetes event log

...sorted by timestamp

```
kubectl get events --sort-by=.metadata.creationTimestamp
```

## pod / deployment memory usage

```shell
kubectl top pods -l app=<appname> --no-headers | awk '{SUM += $3} END { print "Total Memory Usage: " SUM " MiB"}'
```

## port forwarding

you may want to omit `--address=0.0.0.0`

```
kubectl port-forward pod-name-here --address=0.0.0.0 8384:8384
```

**get a random local port:**

```
kubectl port-forward pod-name-here --address=0.0.0.0 :8384
```

## run cronjob manually

get list of cron jobs:

```
kubectl get cronjob
# gickup   0 4 * * * [...]
```

run a manual job:

```
kubectl create job --from=cronjob/gickup gickup-run-manual
```

you might want to delete the job afterwards:

```
kubectl delete job gickup-run-manual
```

## run one-off pod

example, run the `minio/mc` container and override the command to end up in a shell instead of the default `mc` entrypoint

```
kubectl run -i --tty mc --image=minio/mc --command /bin/sh
```

## run pod with registry secrets

update / replace `registry-secret-name` and specify your image after `--image`

```shell
kubectl run -i --tty my-container --image=ghcr.io/example/private-image:latest --command /bin/sh --overrides='{ "spec": { "imagePullSecrets": [{"name": "registry-secret-name"}] } }'
```

## tail logs

this will read the last 100 log entries and also keep following the log for new entries

```shell
kubectl logs -f --tail=100 <pod-name>
```
