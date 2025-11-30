---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: direnv
description: Load/unload environment variables based on directory
os:
  - linux
  - macos
source: Homebrew
url: https://direnv.net
---

# 🔧 direnv

Automatically load and unload environment variables based on the current directory.

## Features

- Per-directory environment variables
- Automatic loading/unloading
- Shell agnostic
- Version manager integration (nvm, rbenv, pyenv)
- Project-specific configuration
- Secure (requires allow before loading)

## Installation

```bash
brew install direnv
```

## Setup

Add to your shell config:

```bash
# For zsh (~/.zshrc)
eval "$(direnv hook zsh)"

# For bash (~/.bashrc)
eval "$(direnv hook bash)"
```

## Usage

```bash
# In your project directory, create .envrc
echo 'export DATABASE_URL=postgres://localhost/mydb' > .envrc

# Allow direnv to load it
direnv allow

# When you cd into the directory, vars are loaded
# When you cd out, they're unloaded
```

## Common Use Cases

### Python virtualenv
```bash
# .envrc
layout python python3
```

### Node.js version
```bash
# .envrc
use node 18
```

### Database URLs
```bash
# .envrc
export DATABASE_URL=postgresql://localhost/dev_db
export REDIS_URL=redis://localhost:6379
```

### API Keys (from .env)
```bash
# .envrc
dotenv
```

### Path modifications
```bash
# .envrc
PATH_add bin
PATH_add node_modules/.bin
```

### Multiple environments
```bash
# .envrc
if [ -f .env.local ]; then
  dotenv .env.local
else
  dotenv
fi

export NODE_ENV=development
```

## Advanced Features

### Load private variables
```bash
# .envrc
source_env_if_exists .envrc.local
```

### Python with specific version
```bash
# .envrc
layout python python3.11
```

### Ruby
```bash
# .envrc
use ruby 3.2.0
```

### Go
```bash
# .envrc
layout go
```

## Security

direnv won't load `.envrc` until you explicitly allow it:

```bash
direnv allow    # Allow current .envrc
direnv deny     # Deny current .envrc
direnv reload   # Reload after changes
```

This prevents malicious code execution from random `.envrc` files.

## Commands

```bash
# Allow .envrc in current directory
direnv allow

# Check status
direnv status

# Reload direnv
direnv reload

# Edit .envrc (automatically allows after save)
direnv edit

# List all loaded variables
direnv export json
```

## Template .envrc

```bash
# .envrc
# Load .env file if it exists
dotenv_if_exists

# Add local bin to PATH
PATH_add bin

# Load Node.js version from .nvmrc
use node

# Load Python virtualenv
layout python python3

# Project-specific variables
export PROJECT_NAME="my-project"
export DEBUG=true
export LOG_LEVEL=debug

# Database
export DATABASE_URL=postgresql://localhost/dev_db

# Load private vars if they exist
source_env_if_exists .envrc.private
```

## Best Practices

1. **Add .envrc to .gitignore** - Don't commit secrets
2. **Use .envrc.private** for secrets
3. **Commit .envrc.example** - Template for team
4. **Always use direnv allow** - Don't disable security
5. **Test in clean shell** - Ensure it works for new users

## With Docker

```bash
# .envrc
export COMPOSE_PROJECT_NAME=${PWD##*/}
export COMPOSE_FILE=docker-compose.yml:docker-compose.dev.yml
```

## Related

- [[mise|mise-en-place]] - Alternative dev environment manager
- [[dotenv]] - Load .env files

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
