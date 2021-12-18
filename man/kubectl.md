# kubectl

see also [kubernetes](/man/kubernetes/)

## get kubernetes event log

...sorted by timestamp

```
kubectl get events --sort-by=.metadata.creationTimestamp
```

## tail logs

this will read the last 100 log entries and also keep following the log for new entries

```
kubectl logs -f --tail=100 <pod-name>
```

## download kubectl for arm architecture, like an raspberry pi

I don't know why they make it so hard, but here you go:

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm/kubectl"
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
