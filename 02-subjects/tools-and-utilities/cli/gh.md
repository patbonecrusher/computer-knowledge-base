---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
  - git
command: gh
description: GitHub official CLI tool
os:
  - linux
  - macos
  - windows
source: Homebrew
url: https://cli.github.com
---

# 🐙 gh

GitHub's official command line tool for working with GitHub from your terminal.

## Features

- Create and manage PRs from command line
- Create and view issues
- Run GitHub Actions workflows
- Clone and fork repositories
- Manage releases
- Manage gists

## Installation

```bash
brew install gh

# Authenticate
gh auth login
```

## Common Usage

```bash
# Create a pull request
gh pr create

# List pull requests
gh pr list

# View PR in browser
gh pr view --web

# Create an issue
gh issue create

# Clone a repo
gh repo clone owner/repo

# Create a repository
gh repo create

# Run a workflow
gh workflow run

# View GitHub Actions runs
gh run list

# Create a gist
gh gist create file.txt
```

## PR Workflow

```bash
# Create PR with title and body
gh pr create --title "Add feature" --body "Description"

# Review a PR
gh pr review

# Merge a PR
gh pr merge

# Check PR status
gh pr checks
```

## Related

- [[02-subjects/tools-and-utilities/cli/git|Git]] - Version control
- [[02-subjects/tools-and-utilities/cli/lazygit|lazygit]] - Git TUI
- [[02-subjects/tools-and-utilities/cli/hub (github)|hub]] - Older GitHub CLI (deprecated in favor of gh)

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
