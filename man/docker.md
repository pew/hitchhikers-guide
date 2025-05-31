---
date created: Monday, December 24th 2018, 3:03:24 pm
date modified: Saturday, May 31st 2025, 10:30:32 am
tags:
  - docker
  - networking
  - ipv6
---

# docker

see also:

- [podman](/man/podman)
- [k3s](/man/k3s)

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

## docker and ipv6

### enable ipv6 with docker compose

create a new `network` to your `compose.yaml` and add this network to your container(s), example:

```yaml
services:
  pihole:
    image: pihole/pihole:latest
    networks:
      - leela-network
    ports:
      - 53:53/tcp
      - 53:53/udp
    environment:
      TZ: Europe/Paris
    volumes:
      - pihole-etc:/etc/pihole
      - pihole-dnsmasq:/etc/dnsmasq.d
    restart: unless-stopped

networks:
  leela-network:
    enable_ipv6: true
```

the above enables ipv6 and ipv4 for your container

### more docker ipv6 stuff

this is for your `/etc/docker/daemon.json` file. it might not exist.

```json
{
  "log-driver": "journald",
  "ipv6": true,
  "fixed-cidr-v6": "fd00:dead:beef:c0::/80",
  "experimental": true,
  "ip6tables": true
}
```
