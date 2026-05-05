# AGENTS.md

## Setup

- Work from the repository root: `fastapi-utils`.
- Install or refresh the development environment with `make develop`.
- The package supports Python 3.8+ and FastAPI `>=0.89,<1.0`.
- Optional extras are `session` for SQLAlchemy support and `all` for SQLAlchemy,
  pydantic-settings, and typing-inspect.

## Testing

- Run the full test suite with `pytest` or `make test`.
- Run coverage with `pytest --cov=fastapi_utils` or `make testcov`.
- Pytest discovers tests under `tests` per `pyproject.toml`.
- For pydantic compatibility checks, use `make ci-v1` and `make ci-v2`.
- Tests use pytest fixtures, `TestClient`, and explicit exception assertions such
  as `with pytest.raises(...)`.

## Style

- Format source and tests with `make format`.
- Check formatting and linting with `make lint`.
- Run type checks with `make mypy`.
- Run the common development checks with `make all` or `make static`.
- Black and Ruff use a 120-character line length for `fastapi_utils` and `tests`;
  docs examples are formatted with Black at 82 characters.
- Keep imports compatible with Ruff/isort's first-party settings for
  `fastapi_utils` and `tests`.
- The codebase uses `from __future__ import annotations` and typed public
  functions; mypy disallows untyped defs.

## Review Guidelines

- Prioritize behavior changes in reusable FastAPI utilities, session handling,
  pydantic v1/v2 compatibility, and optional dependency paths.
- Confirm tests cover both the package code and representative FastAPI usage.
- Watch SQLite tests on Windows: dispose or reset SQLAlchemy engines before
  deleting database files.
- Do not treat warnings as failures unless the change introduces or relies on
  them, but call out new deprecations in reviews.
- Prefer focused changes that match the existing fixture, context manager, and
  pytest assertion patterns.
