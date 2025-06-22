---
date created: Friday, October 4th 2024, 10:27:43 am
date modified: Sunday, June 22nd 2025, 3:35:30 pm
tags:
  - python
---

# uv

> An extremely fast Python package and project manager, written in Rust.

- [github project page](https://github.com/astral-sh/uv)
- see also [pip](/man/pip)

## run executable

this will run `cowsay` in its own virtual environment and execute it directly, similar to `pipx`

```shell
uvx cowsay -t sup
```

## install different python versions

[it uses the latest patch version automatically](https://docs.astral.sh/uv/concepts/python-versions/#installing-a-python-version)

```shell
uv python install 3.13
```

## create virtual environment

*request* a specific python version and create a venv:

```shell
uv venv --python 3.13
```

## clean cache

```shell
uv cache clean
```

## uv tool - install python binaries

install a python binary using `uv tool` right into your `PATH`, not scoped to a project:

```shell
uv tool install yamllint
```

sometimes you need additional binaries with a package, for example ansible. you can use the `--with` flag:

```shell
uv tool install --with ansible ansible-core
```

## managing packages

### install with pip interface

with the `pip` interface

```shell
uv pip install <python package>
```

### add package to project

```shell
uv init
uv add sqlite-utils
```
