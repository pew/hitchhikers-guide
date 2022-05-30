# docker

- [podman](/man/podman)

## exec as other user (e.G. root)

with `docker exec` (where `ac0` is the container id):

```
docker exec -it -u root ac0 sh
```

or with `docker-compose` (znc is the container name):

```
docker-compose exec -u root znc sh
```

## docker logs

the default `json` log can become pretty large if you're running a container for weeks. there are multiple options for [logging](https://docs.docker.com/config/containers/logging/), to simply use syslog globally for all containers:

create or edit `/etc/docker/daemon.json`:

```
{
  "log-driver": "syslog"
}
```

or like this:

```
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  }
}
```

changes in the `daemon.json` only apply to new containers, not existing.

## docker cleanup

get rid of exited containers:

```
docker rm $(docker ps -aq -f status=exited)
```

get rid of unused images:

```
docker rmi $(docker images -a|grep none|awk {'print $3'})
```

## ipv6

this will never end

### enable ipv6 in docker container

I just want my nginx or traefik container to be available from the outside, man. Since I couldn't find anything meaningful out there on the interwebs I assume something is dangerously wrong with my config, but it *works*.

`docker-compose.yaml` example (from mailcow):

```yaml
networks:
  proxynet:
    name: awesomenet
    driver: bridge
    enable_ipv6: true
    ipam:
      driver: default
      config:
        - subnet: fd4d:6169:6c63:6f77::/64
```

### more docker ipv6 stuff

this is for your `/etc/docker/daemon.json` file. it might not exist.

```
{
  "ipv6": true,
  "fixed-cidr-v6": "fd00:dead:beef:c0::/80",
  "experimental": true,
  "ip6tables": true
}
```
