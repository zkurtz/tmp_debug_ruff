# debugging ruff

Problem: `src/__init__.py` contains relative imports, but `ruff check .` fails to raise an associated error even though the `pyproject.toml` says to ban relative imports.
