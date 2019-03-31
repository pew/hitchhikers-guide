# alpine

* development tools/build essentials in alpine is called: `build-base`, install with: `apk add --no-cache build-base`

# virtual packages

use this to create virtual *build* packages and remove them in the final stage

```
apk --update add --virtual build-dependencies python-dev build-base wget \
  && pip install -r requirements.txt \
  && python setup.py install \
  && apk del build-dependencies
```

# add package without cache

```
apk --no-cache add nginx
```

# list installed packages

```
apk info
```
