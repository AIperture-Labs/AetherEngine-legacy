---
name: python-lint
description: Lint Python code with ruff. Use before committing Python changes or when configuring ruff.
---

# Python lint

Run `uv run ruff check` from `python/`. The rules come from the
project's own `pyproject.toml`; don't pass rule flags or override them.
