---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
  - git
command: pre-commit
description: Framework for managing git hooks
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://pre-commit.com
---

# ✅ pre-commit

A framework for managing and maintaining multi-language pre-commit hooks.

## Features

- Automatically run checks before commits
- Multi-language support
- Plugin ecosystem
- Easy configuration
- Prevents bad commits
- Format code automatically

## Installation

```bash
brew install pre-commit
```

## Setup

```bash
# In your git repository
pre-commit install

# Create .pre-commit-config.yaml
cat > .pre-commit-config.yaml << 'EOF'
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-added-large-files
      - id: check-merge-conflict
      - id: check-json
      - id: pretty-format-json
        args: ['--autofix']

  - repo: https://github.com/psf/black
    rev: 23.12.1
    hooks:
      - id: black
EOF
```

## Usage

```bash
# Install hooks
pre-commit install

# Run manually on all files
pre-commit run --all-files

# Run specific hook
pre-commit run black

# Update hooks to latest versions
pre-commit autoupdate

# Uninstall hooks
pre-commit uninstall

# Skip hooks for one commit
git commit --no-verify
```

## Common Hooks

```yaml
# Python
- repo: https://github.com/psf/black
  rev: 23.12.1
  hooks:
    - id: black

- repo: https://github.com/pycqa/flake8
  rev: 7.0.0
  hooks:
    - id: flake8

# JavaScript/TypeScript
- repo: https://github.com/pre-commit/mirrors-eslint
  rev: v8.56.0
  hooks:
    - id: eslint

- repo: https://github.com/pre-commit/mirrors-prettier
  rev: v3.1.0
  hooks:
    - id: prettier

# Go
- repo: https://github.com/dnephin/pre-commit-golang
  rev: v0.5.1
  hooks:
    - id: go-fmt
    - id: go-vet
    - id: go-mod-tidy

# Rust
- repo: https://github.com/doublify/pre-commit-rust
  rev: v1.0
  hooks:
    - id: fmt
    - id: cargo-check
```

## Example Python Project

```.pre-commit-config.yaml
repos:
  # General hooks
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-toml
      - id: check-merge-conflict
      - id: check-added-large-files

  # Python formatting
  - repo: https://github.com/psf/black
    rev: 23.12.1
    hooks:
      - id: black

  # Python linting
  - repo: https://github.com/pycqa/flake8
    rev: 7.0.0
    hooks:
      - id: flake8

  # Import sorting
  - repo: https://github.com/pycqa/isort
    rev: 5.13.2
    hooks:
      - id: isort

  # Type checking
  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.8.0
    hooks:
      - id: mypy
```

## Benefits

- Catch errors before they reach CI
- Enforce code style automatically
- Fast feedback loop
- Prevent commits of large files, secrets, etc.
- Share configuration across team

## Related

- [[02-subjects/tools-and-utilities/cli/git|Git]] - Version control
- [[gh|gh]] - GitHub CLI

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
