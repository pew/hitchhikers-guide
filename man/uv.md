---
date created: Friday, October 4th 2024, 10:27:43 am
date modified: Friday, October 4th 2024, 10:35:30 am
tags:
  - python
---

# uv

> An extremely fast Python package and project manager, written in Rust.

- [github project page](https://github.com/astral-sh/uv)
- see also [pip](pip)

## run executable

this will run `cowsay` in its own virtual environment and execute it directly, similar to pipx

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

## managing packages

### install with pip interface

with the `pip` interface

```shell
uv pip install <python package>
```

### add to project

```shell
uv init
uv add sqlite-utils
```
