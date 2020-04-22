# pytest - python test framework

* [pytest](https://docs.pytest.org/en/latest/)

install like this:

```
pip install pytest
```

## PYTHONPATH - ModuleNotFoundError: No module named

if you get an error like `ModuleNotFoundError: No module named`, provide the path to the tests:

```
python -m pytest tests/
```

## print messages to terminal / console

```
pytest -s
```

