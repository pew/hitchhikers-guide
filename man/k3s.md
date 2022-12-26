---
date created: Sunday, September 12th 2021, 11:38:26 am
date modified: Monday, December 26th 2022, 9:01:14 am
tags:
  - k3s
  - k8s
  - kubernetes
---

# k3s

see also some kubernetes / k8s stuff:

- [kubernetes](/man/kubernetes)
- [kubectl](/man/kubectl)

## cleanup unused images

that's how things start. cleanup unused images, sometimes I need to do that and besides what kubernetes things since other stuff is also running on the same system (I know).

**list images:**

```
sudo k3s crictl images
```

**delete images not currently in use:**

```
sudo k3s crictl rmi --prune
```

[source](https://github.com/k3s-io/k3s/issues/1900#issuecomment-644453072)

## delete individual image

```
sudo k3s crictl rmi docker.pkg.dev/package/packagename:latest
```

## import docker / container image

```shell
docker save localhost/shaarli | sudo k3s ctr images import -
```

you can also run `docker save -o filename localhost/your-local-image` to save the image as a file, move it around and import it then via `k3s ctr images import filename`

**how to use it in a kubernetes yaml file:**

```yaml
containers:
- image: localhost/shaarli:latest
  imagePullPolicy: Never
```
