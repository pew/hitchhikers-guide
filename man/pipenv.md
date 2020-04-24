# pipenv

> Pipenv is a production-ready tool that aims to bring the best of all packaging worlds to the Python world. It harnesses Pipfile, pip, and virtualenv into one single command.

* [pipenv docs](https://pipenv.pypa.io/en/latest/basics/)

## pipenv install / init

```
pipenv install
```

## activate pipenv virtualenv

```
pipenv shell
```

## install packages

**install regular package:**

```
pipenv install package_name
```

**install package as dev dependency:**

```
pip install --dev package_name
```

**install all packages from Pipfile:**

omit or keep `--dev` to include/exclude dev packages

```
pipenv install --dev
```

**uninstall a package:**

```
pipenv uninstall package_name
```

**generate a requirements.txt for a project:**

```
pipenv lock --requirements
```
