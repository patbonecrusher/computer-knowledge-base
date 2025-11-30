---
creation date: 2025-11-29
tags:
  - shell/cli
  - dev/tools
command: fuck
description: Corrects your previous console command
os:
  - linux
  - macos
source: Homebrew
url: https://github.com/nvbn/thefuck
---

# 🤬 thefuck

Magnificent app that corrects errors in previous console commands.

## Features

- Automatically suggests fixes for mistyped commands
- Learns from your mistakes
- Supports many command-line tools
- Customizable rules
- Funny and useful

## Installation

```bash
brew install thefuck
```

## Setup

Add to your shell config (~/.zshrc or ~/.bashrc):

```bash
# For zsh
eval $(thefuck --alias)

# Custom alias
eval $(thefuck --alias FUCK)
```

## Usage

```bash
# Type a command that fails
git psuh origin main

# Then type
fuck

# It will suggest and run
git push origin main
```

## Examples

```bash
# Forgot sudo
$ apt install package
E: Could not open lock file - open (13: Permission denied)
$ fuck
sudo apt install package [enter/↑/↓/ctrl+c]

# Typo in git command
$ git brnch
git: 'brnch' is not a git command. See 'git --help'.
$ fuck
git branch [enter/↑/↓/ctrl+c]

# Wrong directory
$ cd /usr/local/sahre
cd: no such file or directory: /usr/local/sahre
$ fuck
cd /usr/local/share [enter/↑/↓/ctrl+c]

# Missing file extension
$ python script
python: can't open file 'script'
$ fuck
python script.py [enter/↑/↓/ctrl+c]
```

## Common Fixes

- `git` typos
- Missing `sudo`
- Wrong directory paths
- File not found (adds extension)
- `npm` / `yarn` commands
- `docker` commands
- `cd` to similar directory names
- `ls` typos
- `rm` mistakes

## Configuration

```bash
# Edit settings
$EDITOR ~/.config/thefuck/settings.py
```

Example settings:
```python
rules = ['sudo', 'git_push', 'python_command', 'cd_mkdir']
exclude_rules = []
wait_command = 3
require_confirmation = True
no_colors = False
```

## Disable Confirmation

```bash
# In ~/.config/thefuck/settings.py
require_confirmation = False
```

## Slow Shell?

If it slows down your shell:
```bash
# Use lazy loading
function fuck {
    eval $(thefuck --alias)
    fuck
}
```

## Custom Alias

```bash
# Instead of "fuck" use something else
eval $(thefuck --alias please)

# Now use
please
```

## How It Works

1. Reads your previous command
2. Analyzes the error
3. Applies rules to suggest fix
4. Shows suggestion
5. You confirm or select alternative

## Related

- [[fzf|fzf]] - Fuzzy finder
- [[02-subjects/tools-and-utilities/cli/zoxide|zoxide]] - Smart cd

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
