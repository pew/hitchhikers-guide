# pyenv

* [pyenv](https://github.com/pyenv/pyenv) - manage and install a bunch of different python versions and also create virtual environments for each and every project
* [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv)

## configure local python version

**create / init a virtualenv:**

go to your desired folder and do:

```
pyenv virtualenv 3.8.2 venv-name
pyenv local venv-name
```

## pyenv custom pip.conf

to use a custom `pip.conf`, e.G. for [piwheels.org](https://www.piwheels.org) ...

when the virtualenv is loaded / activated, create the custom `pip.conf` like this:

```
vi $PYENV_VIRTUAL_ENV/pip.conf
```
