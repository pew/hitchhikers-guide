# traefik

cool/hipster reverse proxy and/or load balancer.

* [website](https://traefik.io)
* [documentation](https://docs.traefik.io)

I'll write some things in here which helped me in some edge cases I couldn't really find in the documentation but were in fact available.

## middlewares

if you define a middleware it needs to be applied to a router. that's it. they mention it somewhere in the docs but never ever on another page with proper examples.

**`docker-compose.yaml` example**

```yaml
version: "3.7"

services:
  frontend:
    image: some-image-here
    restart: unless-stopped
    labels:
      - "traefik.enable=true"
      - "traefik.docker.network=web"
      - "traefik.http.middlewares.redirect-https.redirectScheme.scheme=https"
      - "traefik.http.middlewares.redirect-https.redirectScheme.permanent=true"

      - "traefik.http.middlewares.no-www.redirectregex.regex=^https://www.(.*)"
      - "traefik.http.middlewares.no-www.redirectregex.replacement=https://$$1"
      
      - "traefik.http.routers.frontend.rule=Host(`ilayk.com`) || Host(`www.ilayk.com`)"
      - "traefik.http.routers.frontend.entrypoints=websecure"

      - "traefik.http.middlewares.frontend-header.headers.browserXssFilter=true"
      - "traefik.http.middlewares.frontend-header.headers.frameDeny=true"
      - "traefik.http.middlewares.frontend-header.headers.contentTypeNosniff=true"
      
      - "traefik.http.middlewares.compress.compress=true"

      - "traefik.http.routers.frontend.middlewares=redirect-https,no-www,compress,frontend-header"
```

the *middlewares* are defined and then applied to the router in the last line.

**basic auth example:**

this is a label excerpt from a `docker-compose.yaml` file

```
  wordpress-www:
    image: wordpress:latest
    restart: unless-stopped
    links:
      - my-db
    labels:
      - "traefik.enable=true"
      - "traefik.docker.network=web"

      - "traefik.http.middlewares.redirect-https.redirectScheme.scheme=https"
      - "traefik.http.middlewares.redirect-https.redirectScheme.permanent=true"

      - "traefik.http.routers.wordpress-www.tls.certresolver=dnsssl"
      - "traefik.http.routers.wordpress-www.tls=true"

      - "traefik.http.middlewares.wordpress-auth.basicauth.users=test2:$$apr1$$d9hr9HBB$$4HxwgUir3HP4EsggP/QNo0"
      - "traefik.http.routers.wordpress-www.middlewares=wordpress-auth"
```

for some reason it works if you take the service name (wordpress-www), create the middleware (2nd last line) and use it again in the last. I have no idea, this is probably totally wrong but it works.

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

**generate username and password hash**:

```
echo $(htpasswd -nbB username "password!1234") | sed -e s/\\$/\\$\\$/g
```

the `sed` part will also directly escape the output suited for a docker label

## priorities

this is very important to understand and it's probably best to always check the [documentation about this here](https://docs.traefik.io/basics/#priorities) - search for *priorities* if they ever change the link. basically routes will be sorted by length in descending order (see http auth example above).

> By default, routes will be sorted (in descending order) using rules length (to avoid path overlap): - `PathPrefix:/foo;Host:foo.com` (length == 28) will be matched before `PathPrefixStrip:/foobar` (length == 23) will be matched before `PathPrefix:/foo,/bar` (length == 20).
