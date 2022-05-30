---
tags: 
date created: Monday, May 30th 2022, 7:07:37 am
date modified: Monday, May 30th 2022, 7:07:37 am
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
