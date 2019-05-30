# python - pip

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
