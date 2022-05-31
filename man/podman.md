---
tags: 
date created: Monday, May 30th 2022, 7:07:37 am
date modified: Tuesday, May 31st 2022, 6:59:13 am
title: podman
---

# podman

docker, podman, buildah... 👋

- see also [docker](/man/docker)

## list all podman containers, including build containers

I was used to get all running and exited containers with docker's `docker ps -a`, however, podman has another place to list containers. Containers started by *buildah*, to build containers. Here's how to list them:

```
podman ps --all --storage
```

## cleanup old / unused containers and images

apparently that's what I do.

just do it like this:

```shell
podman system prune
```

for more detailed things, and also the build images/containers do this:

```shell
podman rm $(podman ps --all -q) # regular containers
podman rm $(podman ps --all --storage -q) # buildah containers
```

get rid of images:

```shell
podman rmi $(podman images -a|grep none|awk {'print $3'})
```
