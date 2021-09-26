# k3s

see also some kubernetes / k8s stuff:

- [kubernetes](/man/kubernetes)
- [kubectl](/man/kubectl)

## cleanup

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

**delete individual image:**

```
sudo k3s crictl rmi docker.pkg.dev/package/packagename:latest
```
