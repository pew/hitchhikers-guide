# docker

yo.

# exec as other user (e.G. root)

with `docker exec` (where `ac0` is the container id):

```
docker exec -it -u root ac0 sh
```

or with `docker-compose` (znc is the container name):

```
docker-compose exec -u root znc sh
```

# docker logs

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

# docker cleanup

get rid of exited containers:

```
docker rm $(docker ps -aq -f status=exited)
```

get rid of unused images:

```
docker rmi $(docker images -a|grep none|awk {'print $3'})
```

