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

