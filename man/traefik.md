# traefik

cool/hipster reverse proxy and/or load balancer.

* [website](https://traefik.io)
* [documentation](https://docs.traefik.io)

I'll write some things in here which helped me in some edge cases I couldn't really find in the documentation but were in fact available. 

## docker labels hints

`$` characters in `docker-compose.yml` files have to be escaped by another `$` = meaning: `$$`

## redirects

www to no-www and http to https

### http to https redirect

this one goes into `traefik.toml` and applies globally

```
[entryPoints]
  [entryPoints.http]
  address = ":80"
    [entryPoints.http.redirect]
    entryPoint = "https"
  [entryPoints.https]
  address = ":443"
  [entryPoints.https.tls]
```

### global: www to no-www redirect

this example applies globally and goes into `traefik.toml`

```
[entryPoints.https.redirect]
permanent=true
regex = "^https://www.(.*)"
replacement = "https://$1"
```

[see also rewriting documentation](https://docs.traefik.io/configuration/entrypoints/#rewriting-url)

### docker(-compose): www to no-www

```
- "traefik.frontend.redirect.regex=^https://www.(.*)"
- "traefik.frontend.redirect.replacement=https://$$1"
- "traefik.frontend.redirect.permanent=true"
```

## multiple domain names

(this is a docker label)

```
- "traefik.frontend.rule=Host:example.com,example2.com"
```

## http basic auth and path rules

suppose you want to protect `/post` and `/edit` endpoints but everything else should work without username/password:

```
- "traefik.docker.network=web"
- "traefik.enable=true"
- "traefik.basic.protocol=http"
- "traefik.basic.frontend.rule=Host:domain.tld,www.domain.tld"
- "traefik.auth.frontend.rule=Host:domain.tld;PathPrefix:/edit,/post"
- "traefik.auth.frontend.auth.basic=jonas:$$2a$$10$asdf"
- "traefik.frontend.redirect.regex=^https://www.(.*)"
- "traefik.frontend.redirect.replacement=https://$$1"
- "traefik.frontend.redirect.permanent=true"
- "traefik.basic.port=8000"
```

this part is the important one:

```
- "traefik.auth.frontend.rule=Host:domain.tld;PathPrefix:/edit,/post"
```

also, the priority evaluation is important, [read about in-depth here](https://docs.traefik.io/basics/#frontends) - I couldn't write it in a way someone can understand it.

[this post also helped me quite a lot](https://stackoverflow.com/q/50253357/10272994)

TODO: htpasswd generator

# todo

* [ ] SSLLabs A+ or something like that

apparently this is out of the box, not verified yet.
