# pip

## updates and upgrades

new is always better!

### list outdated packages

```
pip list --outdated
```

### upgrade package

upgrade pip in this case:

```
pip install -U pip
```

upgrade all outdated packages:

```shell
pip list --outdated --format=json | jq -r '.[] | "\(.name)==\(.latest_version)"' | xargs --no-run-if-empty -n1 pip install -U
```

[thx](https://stackoverflow.com/a/3452888)

### upgrade packages from file

```
pip install -U -r requirements.txt
```

## versioning

put it like this in your `requirements.txt` file to always stick to the latest minor version:

```
gunicorn>=19.9
```

this will install gunicorn `19.9.1` and `19.9.2` and so on.
