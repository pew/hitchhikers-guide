---
date created: Monday, May 30th 2022, 7:07:37 am
date modified: Friday, April 21st 2023, 6:19:24 am
tags:
  - docker
  - podman
  - container
title: podman
---

# podman

docker, podman, buildah... 👋

- see also [docker](/man/docker)

## working with pods

### create a new pod

…which can hold multiple containers (they can then communicate between each other via localhost and exposed ports):

```shell
podman pod create --name lab # without any exposed ports to the host
podman pod create --name lab -p 127.0.0.1:3001:3001 # expose ports to the host
```

### list pods

```shell
podman pod list
```

### add containers to a pod

adding the `uptime-kuma` container and `cloudflared` to the pod. The `cloudflared` tunnel can then be configured as a proxy to proxy requests to `localhost:3001` to expose the `uptime-kuma` container to the web (the whole network exposing thing couldn't be required)

```shell
podman run -dt --restart=unless-stopped --pod lab -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1
podman run -dt --restart=unless-stopped --pod lab cloudflare/cloudflared:latest tunnel --no-autoupdate run --token <asdf-token>
```

## working with containers

### list all podman containers, including build containers

I was used to get all running and exited containers with docker's `docker ps -a`, however, podman has another place to list containers. Containers started by *buildah*, to build containers. Here's how to list them:

```
podman ps --all --storage
```

### update container

pull the new image, stop and delete the old container, re-run the command how you initially started the container to get it back up.

```shell
podman inspect my-container --format "{{.Image}} {{.ImageName}}"
podman pull username/container:latest
podman stop my-container
podman rm my-container
podman run -dt --restart=unless-stopped --pod lab --name my-container username/container:latest
podman inspect my-container --format "{{.Image}} {{.ImageName}}"
```

### cleanup old / unused containers and images

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

## generate systemd / kubernetes definitions

```shell
podman generate --help
```

**generate a kubernetes yaml** file from an existing container/pod:

```shell
podman generate kube my-pod
```

**run kubernetes definition** using podman:

```shell
podman play kube my-pod.yaml
```
