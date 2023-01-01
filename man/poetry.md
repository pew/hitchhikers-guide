---
date created: Sunday, January 1st 2023, 11:14:01 am
date modified: Sunday, January 1st 2023, 11:23:50 am
tags:
  - python
  - poetry
  - pip
  - venv
---

# poetry

[the official docs and project description might be a better resource](https://python-poetry.org/) if you want to get started. this page is more like a quick cheat sheet

## creating a project

**create new project:**

```shell
poetry new project-name
```

**use poetry in an existing project:**

```shell
poetry init
```

## package management

**install packages defined in `pyproject.toml`:**

```shell
poetry install
```

**add package:**

```shell
poetry add feedparser
```

**delete / remove package:**

```shell
poetry remove pendulum
```

**update packages:**

```shell
poetry update
```

## use poetry virtualenv

depending on your config, the virtual environment poetry creates is automatically activated, if not, do this:

```shell
poetry shell
```

if the above doesn't work for some reason, that's how I got it working otherwise:

```shell
source `poetry env info --path`/bin/activate
```

## run scripts

```shell
poetry run python your_script.py
```

if a package you've added comes with an executable CLI tool, you can run them like this:

```shell
poetry run black
poetry run pytest
```
