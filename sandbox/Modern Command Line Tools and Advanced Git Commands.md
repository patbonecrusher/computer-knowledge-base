---
creation date: 2024-11-04 13:30
tags:
  - references/best-of
  - shell/cli
---
---

```cardlink
url: https://medium.com/otto-group-data-works/developer-hacks-modern-command-line-tools-and-advanced-git-commands-e3724dab00a1
title: "Developer Hacks — Modern Command Line Tools and Advanced Git Commands"
description: "Working with the terminal and with Git are among the basic techniques for developers. This article presents a modern development setup…"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/resize:fit:1200/1*ZfR0lWiO4X00_nwj0kxaig.png
```


Working with the terminal and with Git are among the basic techniques for developers. This article presents a modern development setup, state-of-the-art alternatives to classic shell programs, and advanced git commands. Using these tools will help you navigate your projects with greater ease and speed, allowing you to focus on what truly matters: building great software.

# Terminal Setup for Mac

For Mac users, [iTerm2](https://iterm2.com/) offers more features than the default Mac terminal app: split panes, hotkey windows, and extensive configurability. Personally, I use it with the [Catppuccin Macchiato](https://github.com/catppuccin/iterm) color theme and especially like its feature of having a scratchpad terminal quickly available via hotkey:

![](https://miro.medium.com/v2/resize:fit:960/1*NTwFkvxdcBCCe6gZTGs2jA.gif)

To further enhance productivity, consider using [Rectangle](https://rectangleapp.com/) for window management, [Alt-Tab](https://alt-tab-macos.netlify.app/) for window switching and [Maccy](https://github.com/p0deje/Maccy) for clipboard history.

# Shell: zsh and others

Zsh, one of the most popular shells and the default on Mac, can be customized with [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh), a framework that simplifies the management of zsh configurations. It is often used with the [powerlevel10k](https://github.com/romkatv/powerlevel10k) prompt for an aesthetically pleasing and informative terminal prompt. Additionally, you can enhance your zsh experience with plugins like [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) or [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting).

![](https://miro.medium.com/v2/resize:fit:1388/1*4r8cSdmS61g2PF2mlEL4Wg.png)

zsh with transient prompt (hide full prompt on past commands), git infos, syntax highlighting (valid command shown green) and auto suggestions

Newer, but less common shells are nushell, fish, and xonsh. To me, [xonsh](https://github.com/xonsh/xonsh)looks particularly interesting as it allows mixing both Python and shell commands.

# Modern Shell Commands

For many of the classic commands like _ls_, _cat_, _find_ etc., there exist modern alternatives. Compared to their traditional counterparts, those shell commands are often faster (as they are often written in Rust), more colorful and more convenient, e.g. by respecting gitignore files.

## ls alternatives: eza and lsd

[_eza_](https://github.com/eza-community/eza) and [_lsd_](https://github.com/lsd-rs/lsd) both provide a better file listing with color highlighting, icons, and additional configurability.

![](https://miro.medium.com/v2/resize:fit:1400/1*2WV5AOMwP-tRPslH2O1zmg.png)

Output comparison for ls, lsd, eza and eza with additional options.

## bat: cat with wings

A text file viewer, [_bat_](https://github.com/sharkdp/bat) uses line numbers, syntax highlighting and git changes. It uses paging for longer output (scroll text like with _less_), but defaults to plain printing when used for piping.

![](https://miro.medium.com/v2/resize:fit:1312/1*EueMtDdYdcDwsyNgWEWSWA.png)

Viewing an HTML file with _bat_, including syntax highlighting and Git integration.

## du to dust

For showing file and folder sizes, [_dust_](https://github.com/bootandy/dust) provides a better sorted and visualized output than the classic _du_:

![](https://miro.medium.com/v2/resize:fit:1400/1*osImUOKnDgNf2RvmtelA3g.png)

## fd: a better find

[_fd_](https://github.com/sharkdp/fd) is a modern alternative to _find_ to search for files, much faster and with cleaner syntax: _fd PATTERN_ instead of _find -iname ‘*PATTERN*’_.

## RIP, grep: ripgrep

A tool for searching text in files. Using sensible default, [_ripgrep_](https://github.com/BurntSushi/ripgrep) considers gitignore rules and ignores hidden and binary files. Several times faster than the original _grep_.

## sed to sd

_sed_ is typically used for replacing text. _sd_ does this with an simpler syntax:

![](https://miro.medium.com/v2/resize:fit:766/1*2E_tJPE7ULJ5hj_DdDa6BA.png)

## htop alternatives: bottom, glances and btop

For the classic _htop_ tool to check system status, modern alternatives are for example [_bottom_](https://github.com/ClementTsang/bottom), [_glances_](https://github.com/nicolargo/glances) or [_btop_](https://github.com/aristocratos/btop) (there exist even more). Although they largely use the same system metrics, they differ in their customizability and how the display and visualize data:

![](https://miro.medium.com/v2/resize:fit:1400/1*ZfR0lWiO4X00_nwj0kxaig.png)

htop & btop (top row), glances & btm (bottom row)

## fzf: Fuzzy finder

[fzf](https://github.com/junegunn/fzf) searches text with a so-called fuzzy search: It will also find slightly different spellings, with characters omitted. Text files, shell history or the output of other commands.The [fzf-zsh-plugin](https://github.com/unixorn/fzf-zsh-plugin) lets you automatically search your command history with fzf when you type ^R.

## What the fuck

The tool [The Fuck](https://github.com/nvbn/thefuck) auto-corrects typing errors in console commands. Instead of going back and manually fixing your typo, just enter fuck and it will suggest the correct command (that you can immediately execute with enter):

![](https://miro.medium.com/v2/resize:fit:562/1*ly9k3dFUmoy9RaPSQPXgYw.png)

# Advanced git commands

Apart from everyday’s commands — git init, clone, git pull, add, commit, git push , diff or show — there exist some git features which can make your life considerably easier in many situations. Let me give a git commands overview of these helpful features.

## (Global) config options

A few helpful options are (set with _git config –global_):

- _merge.conflictstyle zdiff3_: For merge conflicts, display the original lines in addition to the diverged versions
- _pull.rebase true_: Always rebase your local branch if the upstream branch has additional commits
- _push.autoSetupRemote true_: When running _git push_ on a local branch, always set up the corresponding remote branch
- _core.pager delta_: Use [delta](https://github.com/dandavison/delta) to display output of e.g. git diff

## Nicer log with git oneline

The output of _git log_ can be shortened with _git log — pretty=oneline_ and made even prettier with custom formatting, e.g. (s[ource](https://ma.ttias.be/pretty-git-log-in-one-line/)):

_git log — graph — pretty=format:’%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset’ — abbrev-commit_

This can be set to an alias via _git config — global alias.logline “log –graph …_

![](https://miro.medium.com/v2/resize:fit:1400/1*a8mpW0g7HyXUeWT-JZT17Q.png)

Output of _git log_ with custom formatting

## Cleaning up a feature branch with interactive rebase

Git’s interactive rebase can be used edit commit history by merging commits, editing their messages or dropping some of them. This is convenient when e.g. cleaning up a feature branch before merging. _git rebase -i_ opens a lists of commits in an editor where you can change the default “pick” to whatever command fits. See a detailed description [here](https://about.gitlab.com/blog/2020/11/23/keep-git-history-clean-with-interactive-rebase/).

## Hunting bugs with git bisect

Imagine the following scenario: Your code is not working properly, but you can’t figure out what’s wrong. You just know that a week ago, everything ran fine.

Git bisect can help you pinpoint the exact commit a bug was introduced. You run _git bisect start_, mark the good and bad commits (with _git bisect good / git bisect bad {hash}). Git will automatically switch to the commit in the middle. You can mark it as good or bad and then git will switch again to commit in the middle between the good and bad commit, repeating this process until the guilty commit was found.

![](https://miro.medium.com/v2/resize:fit:1400/1*13-d1HqrvNKo5PXcDuNiRQ.png)

Starting with a bad (step 1) and good (step 2) commit, _git bisect_ will jump to the commits in between (steps 3 and 4) to narrow down the commit where an error was introduced (step 5).

## Finding lost stuff with git reflog

Accidentally deleted a branch or lost a commit? Don’t worry, these are still in git! You can use _git reflog_ to get a list of previous commits/branches you were on and find the hash of the deleted object (and then use git checkout to restore it):

![](https://miro.medium.com/v2/resize:fit:1400/1*iLGqRXebDARie7rza_jIjw.png)

# Switching to another branch with git worktree

Let’s say you’re working on a feature, and you have many edited or new files. Suddenly, you have to fix a commit on the main branch. You’d typically either commit and stash your changes and switch to main or create another copy of the entire repository somewhere else to have a clean state.

With git worktree, you can create another worktree, something like “a copy of the repo inside your repo”, which you can delete after making changes:

```sh
git worktree add ./fix-critical-bug main  
# go to the fix-critical-bug directory, commit and push solution on the main branch  
git worktree remove ./fix-critical-bug  
# return to working on your feature
```

In conclusion, by integrating these modern command line tools and advanced Git commands into your workflow, you can enhance your productivity and focus on crafting software that creates real business value.