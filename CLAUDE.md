# CLAUDE.md

## Project Overview

LEGO Block Creator is an offline CLI inventory tracking application for managing LEGO parts and sets. Written in pure Python 3.9+ with no runtime dependencies. Currently in alpha (v0.4.0).

## Commands

```bash
# Run the app
python main.py

# Run tests (21 tests, 100% coverage target)
pytest
pytest -v                        # verbose
pytest tests/test_main.py::test_lego_cmd_newpiece  # single test

# Lint
pylint $(git ls-files '*.py')

# Build for PyPI
python -m build

# Docker
docker build .
docker-compose up
```

## Project Structure

- `main.py` — Core CLI logic (all commands, interactive loop)
- `__main__.py` — Module entry point
- `__init__.py` — Package init
- `tests/test_main.py` — All unit tests (unittest.mock for input/print)
- `docs/` — Usage, testing, and CI/CD documentation
- `.github/workflows/` — CI: pytest (3 OS × 4 Python), pylint, CodeQL, Docker publish, PyPI publish
- `.github/agents/` — AI agent prompts for lint, test, docs, and API tasks

## Code Conventions

- **Indentation:** 4 spaces, no tabs
- **Comments:** Heavy inline comments expected (per CONTRIBUTING.md)
- **Naming:** CamelCase for variables (`INPUTmain`, `PIECESall`), snake_case for functions
- **Versioning:** Semantic Versioning
- **Linting:** Must pass pylint
- **Tests:** pytest with unittest.mock; function names start with `test_`; 100% coverage target
- **Dependencies:** No runtime deps. Test deps: pytest, pytest-cov

## CI/CD

All workflows run via GitHub Actions:
1. `pytest.yml` — Tests on push/PR across 12 environments
2. `pylint.yml` — Lint on every push
3. `codeql-analysis.yml` — Security scanning
4. `docker-publish.yml` — Docker image on release
5. `push-to-pypi.yml` — PyPI publish on release

## Key Notes

- The app does not persist data to a database yet (planned for v1.0.0)
- Interactive CLI loop: prompts `LEGO CMD:` and accepts 23+ commands
- Contribution model: GitHub Flow (see CONTRIBUTING.md)
