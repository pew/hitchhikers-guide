# kubernetes / k8s

this is going to be a big one. see also [kubectl](/man/kubectl/)

## rancher, canal, flannel listen on network interface

I use wireguard to tunnel traffic between kubernetes nodes. When setting up a new *rancher* cluster, you can put in all your information in a GUI, set canal as the default network driver. afterwards **edit the YAML** part and go look for `network`. in there you can change the networking interface for the driver

```yaml
network: 
  canal_network_provider: 
    iface: "wg0"
  options: 
    flannel_backend_type: "vxlan"
  plugin: "canal"
```

the `iface` part is important

## reisze aws-ebs

* [some sources, most of it was mine](https://kubernetes.io/blog/2018/07/12/resizing-persistent-volumes-using-kubernetes/) | [even more here](https://akomljen.com/easy-way-to-resize-kubernetes-persistent-volumes/)

1. edit the storageclasses first

```
kubectl get storageclass
kubectl edit storageclass
```

```
[...]
parameters:
  fsType: ext4
  type: gp2
allowVolumeExpansion: true
```

make note of the added `allowVolumeExpansion`.

2. edit the volume claim

```
kubectl edit pvc gitlab-minio
```

```
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 100Gi
  storageClassName: gp2
  volumeName: pvc-9ef67592-1d5e-11e9-857d-0a8271abe0a2
```

change the `storage` part.

3. see status

```
kubectl describe pvc gitlab-redis
```

```
Conditions:
  Type       Status  LastProbeTime                     LastTransitionTime                Reason  Message
  ----       ------  -----------------                 ------------------                ------  -------
  Resizing   True    Mon, 01 Jan 0001 00:00:00 +0000   Wed, 23 Jan 2019 08:58:57 +0100           
```

it'll change to something like that hopefully:

```
Conditions:
  Type                      Status  LastProbeTime                     LastTransitionTime                Reason  Message
  ----                      ------  -----------------                 ------------------                ------  -------
  FileSystemResizePending   True    Mon, 01 Jan 0001 00:00:00 +0000   Wed, 23 Jan 2019 09:07:29 +0100           Waiting for user to (re-)start a pod to finish file system resize of volume on node.
Events:                     <none>
Mounted By:                 gitlab-redis-7b9d4587f8-v8jgw
```

afterwards you can delete the pod to re-create it (if you've got a replicaset hopefully to do that)

```
kubectl delete pod gitlab-redis-7b9d4587f8-v8jgw
```

## suspend all cronjobs

to disable / suspend all cronjobs, do this:

```
kubectl get cronjobs | grep False | cut -d' ' -f 1 | xargs kubectl patch cronjobs -p '{"spec" : {"suspend" : true }}'
```

re-enable like this:

```
kubectl get cronjobs | grep True | cut -d' ' -f 1 | xargs kubectl patch cronjobs -p '{"spec" : {"suspend" : false }}'
```

[source](https://stackoverflow.com/a/55090194/10272994)

## stop kubernetes deployment

set the replicas to 0, it'll delete the pods and the deployment will stay intact.

```
kubectl scale --replicas=0 deployment <deployment-name>
```
