Problem: `src/__init__.py` contains relative imports, but `ruff check .` fails to raise an associated error even though the `pyproject.toml` [says to ban relative imports](https://github.com/zkurtz/tmp_debug_ruff/blob/8e5e69d966ab67d928ba7b8bcc15a06b2207cf05/pyproject.toml#L15-L17).

## Set up

1. Install poetry: `curl -sSL https://install.python-poetry.org | python3 -`
1. Install [pyenv and its virtualenv plugin](https://github.com/pyenv/pyenv-virtualenv).
1. Create a dev ops virtual environment:
```
PYTHON_VERSION=3.12.2
function makenv {
    pyenv install $PYTHON_VERSION --skip-existing
    pyenv global $PYTHON_VERSION
    pyenv virtualenv $PYTHON_VERSION $1
    pyenv activate $1
    poetry install
    poetry lock --no-update
}
makenv tmp_debug_ruff
```