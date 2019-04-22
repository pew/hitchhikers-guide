# traefik

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

# todo

* [ ] SSLLabs A+ or something like that

apparently this is out of the box, not verified yet.

* [ ] http basic auth for some routes or everything

[here's a possible solution](https://stackoverflow.com/q/50253357/10272994)
