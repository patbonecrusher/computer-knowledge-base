---
creation date: 2024-11-04 13:30
tags:
  - dev/tools
  - shell/cli
command: git
description: source control
os:
  - linux
  - macos
  - windows
source: Installed by default
url: https://git-scm.com
---
## how to have a global git ignore

```bash
echo ".DS_Store" >> ~/.gitignore_global
echo "._.DS_Store" >> ~/.gitignore_global
echo "**/.DS_Store" >> ~/.gitignore_global
echo "**/._.DS_Store" >> ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

## Switching to another branch with git worktree

Let’s say you’re working on a feature, and you have many edited or new files. Suddenly, you have to fix a commit on the main branch. You’d typically either commit and stash your changes and switch to main or create another copy of the entire repository somewhere else to have a clean state.

With git worktree, you can create another worktree, something like “a copy of the repo inside your repo”, which you can delete after making changes:

```sh
git worktree add ./fix-critical-bug main  
# go to the fix-critical-bug directory, commit and push solution on the main branch  
git worktree remove ./fix-critical-bug  
# return to working on your feature
```

## Hunting bugs with git bisect

Imagine the following scenario: Your code is not working properly, but you can’t figure out what’s wrong. You just know that a week ago, everything ran fine.

Git bisect can help you pinpoint the exact commit a bug was introduced. You run _git bisect start_, mark the good and bad commits (with `git bisect good / git bisect bad <hash>`). Git will automatically switch to the commit in the middle. You can mark it as good or bad and then git will switch again to commit in the middle between the good and bad commit, repeating this process until the guilty commit was found.

![](Pasted%20image%2020241110225852.png)

Starting with a bad (step 1) and good (step 2) commit, _git bisect_ will jump to the commits in between (steps 3 and 4) to narrow down the commit where an error was introduced (step 5).

## Renaming local and remote branches

```
❯ git branch -m {old_branch_name} {new_branch_name}
❯ git push origin :{old_remote_branch_name} {new_remote_branch_name}
❯ git push --set-upstream origin {new_remote_branch_name}
Everything up-to-date
```



```cardlink
url: https://medium.com/the-syntax-diaries/git-commands-that-saved-our-1m-project-and-will-save-yours-too-8655413178c2
title: "Git Commands That Saved Our $1M Project (And Will Save Yours Too)"
description: "How our team recovered from disaster using these lesser-known Git techniques"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/resize:fit:1200/1*cXeO3PjRFsXngtBwKolKmg.png
```

```cardlink
url: https://medium.com/@kuldeepkumawat195/mastering-git-20-essential-git-command-line-tricks-every-developer-should-know-4e0e0e616a20
title: "Mastering Git: 20 Essential Git Command-Line Tricks Every Developer Should Know"
description: "Git is the backbone of modern version control systems, and most developers use it daily. However, many only scratch the surface of what it…"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/resize:fit:1200/1*5bXwRLH_GaHtcHitf1r8_Q.png
```

