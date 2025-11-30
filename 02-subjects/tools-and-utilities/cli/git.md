---
creation date: 2024-11-04 13:30
tags:
  - shell/cli
  - dev/tools
  - version-control
command: git
description: Distributed version control system
os:
  - linux
  - macos
  - windows
source: Installed by default
url: https://git-scm.com
---

# 🌲 Git

Distributed version control system - track changes, collaborate, and manage code history.

## Features

- Distributed version control
- Branching and merging
- Staging area for commits
- Local and remote repositories
- Commit history and diff viewing
- Tag releases
- Stash changes
- Rebase and cherry-pick
- Worktrees for parallel work

## Installation

```bash
# macOS (pre-installed, update with Homebrew)
brew install git

# Linux
sudo apt install git  # Debian/Ubuntu
sudo yum install git  # RHEL/CentOS
```

## Initial Setup

```bash
# Set identity
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Set default editor
git config --global core.editor "nvim"

# Enable color output
git config --global color.ui auto

# View configuration
git config --list
```

## Common Usage

### Basic Workflow

```bash
# Initialize repository
git init

# Clone repository
git clone https://github.com/user/repo.git

# Check status
git status

# Add files to staging
git add file.txt
git add .  # Add all changes

# Commit changes
git commit -m "Add feature"

# Push to remote
git push origin main

# Pull from remote
git pull origin main

# View commit history
git log
git log --oneline
git log --graph --all
```

### Branching

```bash
# List branches
git branch
git branch -a  # Include remote branches

# Create new branch
git branch feature-x

# Switch to branch
git checkout feature-x
# Or create and switch in one command
git checkout -b feature-x

# Modern syntax (Git 2.23+)
git switch feature-x
git switch -c feature-x  # Create and switch

# Merge branch
git checkout main
git merge feature-x

# Delete branch
git branch -d feature-x  # Safe delete
git branch -D feature-x  # Force delete

# Delete remote branch
git push origin --delete feature-x
```

### Viewing Changes

```bash
# Show changes in working directory
git diff

# Show staged changes
git diff --staged

# Show changes in specific file
git diff file.txt

# Show commit details
git show <commit-hash>

# Show file at specific commit
git show <commit-hash>:path/to/file
```

## Configuration

### Global Git Ignore

```bash
# Create global ignore file
echo ".DS_Store" >> ~/.gitignore_global
echo "._.DS_Store" >> ~/.gitignore_global
echo "**/.DS_Store" >> ~/.gitignore_global
echo "**/._.DS_Store" >> ~/.gitignore_global
echo ".idea/" >> ~/.gitignore_global
echo ".vscode/" >> ~/.gitignore_global
echo "*.swp" >> ~/.gitignore_global

# Configure Git to use it
git config --global core.excludesfile ~/.gitignore_global
```

### Useful Aliases

```bash
# Add to ~/.gitconfig or use git config --global alias.<name> <command>

[alias]
  st = status
  co = checkout
  br = branch
  ci = commit
  unstage = reset HEAD --
  last = log -1 HEAD
  visual = log --graph --oneline --all
  amend = commit --amend --no-edit
  undo = reset --soft HEAD~1
  # Show files in last commit
  changed = diff --name-only HEAD~1 HEAD
```

## Advanced Usage

### Git Worktree

Work on multiple branches simultaneously without stashing:

```bash
# Create worktree for main branch
git worktree add ./fix-critical-bug main

# Go to the worktree directory, make changes, commit
cd fix-critical-bug
# ... make changes ...
git add .
git commit -m "Fix critical bug"
git push

# Return to main directory
cd ..

# Remove worktree when done
git worktree remove ./fix-critical-bug

# List all worktrees
git worktree list
```

### Git Bisect

Find the commit that introduced a bug:

```bash
# Start bisect session
git bisect start

# Mark current commit as bad
git bisect bad

# Mark known good commit
git bisect good <commit-hash>

# Git will checkout middle commit
# Test and mark as good or bad
git bisect good  # or git bisect bad

# Repeat until Git finds the culprit
# Git will tell you which commit introduced the bug

# End bisect session
git bisect reset
```

### Interactive Rebase

Clean up commit history before pushing:

```bash
# Rebase last 3 commits
git rebase -i HEAD~3

# In the editor:
# pick = keep commit
# reword = change commit message
# squash = merge with previous commit
# fixup = like squash, discard message
# drop = remove commit

# Example:
# pick abc123 Add feature
# squash def456 Fix typo
# reword ghi789 Update docs
```

### Stashing

Temporarily save changes:

```bash
# Stash changes
git stash

# Stash with message
git stash save "WIP: feature X"

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply and remove stash
git stash pop

# Apply specific stash
git stash apply stash@{2}

# Show stash contents
git stash show -p stash@{0}

# Drop stash
git stash drop stash@{0}

# Clear all stashes
git stash clear
```

### Cherry-pick

Apply specific commits to current branch:

```bash
# Cherry-pick single commit
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick <hash1> <hash2>

# Cherry-pick range
git cherry-pick <hash1>..<hash2>
```

### Branch Management

```bash
# Rename local branch
git branch -m old-name new-name

# Rename current branch
git branch -m new-name

# Rename local and remote branch
git branch -m old-name new-name
git push origin :old-name new-name
git push --set-upstream origin new-name

# Track remote branch
git branch --set-upstream-to=origin/main main
```

### Undoing Changes

```bash
# Discard changes in working directory
git checkout -- file.txt
# Or with modern syntax
git restore file.txt

# Unstage file
git reset HEAD file.txt
# Or
git restore --staged file.txt

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert commit (creates new commit)
git revert <commit-hash>
```

## Workflows

### Feature Branch Workflow

```bash
# Create feature branch
git checkout -b feature/new-feature

# Work and commit
git add .
git commit -m "Implement feature"

# Push feature branch
git push -u origin feature/new-feature

# Create pull request (using gh CLI)
gh pr create --title "New Feature" --body "Description"

# After merge, cleanup
git checkout main
git pull
git branch -d feature/new-feature
```

### Hotfix Workflow

```bash
# Create hotfix worktree
git worktree add ../hotfix main

# Fix, commit, and push
cd ../hotfix
# ... make fixes ...
git add .
git commit -m "Fix critical issue"
git push

# Clean up
cd ../main-repo
git worktree remove ../hotfix
git pull  # Get the hotfix
```

## Integration

### With GitHub CLI

```bash
# Install gh
brew install gh

# Authenticate
gh auth login

# Create PR
gh pr create

# View PRs
gh pr list

# Checkout PR
gh pr checkout 123
```

### With Delta (Better Diffs)

```bash
# Install delta
brew install git-delta

# Configure Git to use delta
git config --global core.pager "delta"
git config --global interactive.diffFilter "delta --color-only"
git config --global delta.navigate true
git config --global delta.side-by-side true
```

### With Lazygit

```bash
# Install lazygit
brew install lazygit

# Launch in repo
lazygit
```

## Worktree Helper Function

Add to `~/.zshrc`:

```zsh
function gwa() {
  if [ -z "$1" ]; then
    echo "Usage: gwa <branch-name>"
    return 1
  fi

  local branch="$1"
  local repo_root
  repo_root=$(git rev-parse --show-toplevel)
  local repo_name
  repo_name=$(basename "$repo_root")
  local branch_short="${branch:0:15}"
  local worktree_folder="../${repo_name}-${branch_short}"

  echo "🚀 Setting up worktree at: $worktree_folder"

  # Fetch latest branches
  git fetch origin

  # Check if the branch exists remotely
  if git ls-remote --exit-code --heads origin "$branch" >/dev/null; then
    echo "🌍 Checking out existing remote branch '$branch'..."
    git worktree add --track -b "$branch" "$worktree_folder" origin/"$branch"
  elif git show-ref --verify --quiet "refs/heads/$branch"; then
    echo "🔄 Branch '$branch' exists locally. Creating worktree..."
    git worktree add "$worktree_folder" "$branch"
  else
    echo "🌱 Creating new branch '$branch' in a new worktree..."
    git worktree add -b "$branch" "$worktree_folder"
  fi

  # Copy .env if it exists
  if [ -e "$repo_root/.env" ]; then
    echo "📄 Copying .env..."
    cp "$repo_root/.env" "$worktree_folder/.env"
  fi

  # Fresh install node_modules
  echo "📦 Checking for node Dependencies..."
  if [ -f "$repo_root/yarn.lock" ]; then
    (cd "$worktree_folder" && yarn install)
  elif [ -f "$repo_root/package-lock.json" ]; then
    (cd "$worktree_folder" && npm install)
  elif [ -f "$repo_root/pnpm-lock.yaml" ]; then
    (cd "$worktree_folder" && pnpm install)
  fi

  echo "✅ Worktree setup complete!"
  cd "$worktree_folder"
}
```

## Troubleshooting

### Common Issues

**Merge conflicts:**
```bash
# View conflicted files
git status

# Open file and resolve conflicts (between <<<< and >>>>)
# Or use merge tool
git mergetool

# After resolving
git add resolved-file.txt
git commit
```

**Detached HEAD state:**
```bash
# Create branch from detached HEAD
git checkout -b new-branch-name

# Or discard and return to main
git checkout main
```

**Reset to remote:**
```bash
# Discard all local changes
git fetch origin
git reset --hard origin/main
```

**Recover deleted commit:**
```bash
# Find commit in reflog
git reflog

# Restore commit
git checkout <commit-hash>
git checkout -b recovered-branch
```

**Large file issues:**
```bash
# Remove file from history
git filter-branch --tree-filter 'rm -f large-file.bin' HEAD

# Or use BFG Repo-Cleaner (faster)
brew install bfg
bfg --delete-files large-file.bin
```

## Tips

- Commit early and often
- Write descriptive commit messages
- Use branches for features and fixes
- Pull before pushing to avoid conflicts
- Use `.gitignore` to exclude build artifacts
- Review changes before committing: `git diff`
- Use `git add -p` for selective staging
- Create tags for releases: `git tag v1.0.0`
- Use worktrees instead of stashing for context switching
- Set up global `.gitignore` for IDE and OS files
- Use `git bisect` to find bug-introducing commits

## Security

```bash
# Sign commits with GPG
git config --global commit.gpgsign true

# Verify signatures
git log --show-signature

# Use SSH for authentication (recommended)
git config --global url."git@github.com:".insteadOf "https://github.com/"
```

## Related

- [[gh|GitHub CLI]] - GitHub integration
- [[02-subjects/tools-and-utilities/cli/lazygit|lazygit]] - Terminal UI for Git
- [[git-delta|git-delta]] - Better diff viewer
- [[tig|tig]] - Text-mode interface for Git
- [[hub|hub]] - Git wrapper with GitHub features

---

**Back to:** [[tools-and-utilities|Tools & Utilities]]
