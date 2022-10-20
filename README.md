# Data of Agamotto - Data Lib

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/claimfy/cfy-infinity-arc">
    <img src="https://raw.githubusercontent.com/claimfy/claimfy/main/images/eye-of-agamotto-pixel-art.png" alt="Logo" width="80" height="60">
  </a>

  <h3 align="center">Data of Agamotto</h3>

</div>

## Description


## Getting Started

### Dependencies

#### Requirements

- python 3.10.5
- pyenv
- poetry

Go to the agamotto lib directory

```bash
cd libs/agamotto/
```

Set the local version of python with pyenv

```bash
pyenv local 3.10.5

poetry env use 3.10.5

poetry install
```

## Lib Structure

### Directory Layout

```bash
.
├── /agamotto/                # Lib directory
│   ├── /data_lib/            # Data Lib Facade interface
│   ├── /models/              # Models of database
│   ├── /repositories/        # Repositories to access db
│   ├── /schemas/             # Schemas to responses
├── /alembic/                 # Migrations
│   ├── /versions/            # Versioning mof migrations
├── /tests/                   # Integration Tests
│   ├── /data_lib/            # Data Lib Tests
│   ├── /repositories/        # Repositories Tests
│   ├── /support/             # Support for the tests
├── poetry.lock               # Poetry lock file
├── pyproject.toml            # Poetry project to manage dependencies
```

## Acknowledgments

Inspiration, code snippets, etc.

- [Poetry](https://python-poetry.org/)

---

Made with ♥ by Claimfy (https://github.com/claimfy)
​
