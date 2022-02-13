# rabbitmqctl

## list queues

```
rabbitmqctl list_queues
```

example with a kubernetes statefulset:

```
kubectl exec rabbitmq-0 -- rabbitmqctl list_queues
```

## purge queue

after listing the queues, why not purge one:

```
rabbitmqctl purge_queue preview
```

and again, a kubernetes example:

```
kubectl exec rabbitmq-0 -- rabbitmqctl purge_queue queue_name
```
