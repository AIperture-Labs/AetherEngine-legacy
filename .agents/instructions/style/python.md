# Python style

Applies to every Python file in the repo, never to `extern/`. Python is the
engine's scripting and tooling layer, under `python/`: automation of engine
actions, bridges to external tools (Blender, FreeCAD…) and plugins. The
build-time scripts run by CMake follow the same rules.

- `python/` is a uv project. `python/pyproject.toml` is the single config
  file: `src/aether/` layout, tests in `python/tests/`, dev tools in the `dev`
  extra, `requires-python = ">=3.14"` (`AETHER_ENGINE_PYTHON_VERSION`).
  uv manages the interpreter, the environment and `uv.lock`, which is
  committed.
- Code that runs inside a host application (a Blender or FreeCAD add-on)
  uses the host's interpreter: such a package declares its own
  `requires-python` and sticks to the syntax that version supports.
- Python 3.14; use native syntax: `list[str]`, `dict[str, int]`, `X | None`.
  No `from __future__ import annotations`, no `typing.List` / `Optional`.
- Type hints are mandatory on every function: all parameters and the return
  type.
- Four spaces for indentation, lines up to 120 characters.
- `_name` is module-private. `__name` is for class internals ("protected",
  name-mangled).
- One line when the statement and its action are short:
  `if not items: return`, `for x in xs: seen.add(x)`.
- Simple conditional assignment is a ternary, not an `if`/`else` block:
  `label = "items" if items else "none"`.
- ruff config in `pyproject.toml`: `line-length = 120`,
  `target-version = "py314"`, rules `E`, `F`, `I`, `UP`, `B`, ignoring `E701`
  and `E702` (one-line statements). Don't run `ruff format`: it expands
  one-line statements.
