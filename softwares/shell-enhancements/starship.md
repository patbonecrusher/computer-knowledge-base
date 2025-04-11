---
creation date: 2024-11-04 22:14
modification date: Monday, 4th November 2024, 22:14:05
tags:
  - shell/prompts
  - shell/enhancements
description: Nice looking prompt written in rust
os:
  - linux
  - macos
  - windows
source: brew
url: https://starship.rs
---
---
```cardlink
url: https://starship.rs
title: "Starship: Cross-Shell Prompt"
description: "Starship is the minimal, blazing fast, and extremely customizable prompt for any shell! Shows the information you need, while staying sleek and minimal. Quick installation available for Bash, Fish, ZSH, Ion, Tcsh, Elvish, Nu, Xonsh, Cmd, and Powershell."
host: starship.rs
favicon: https://starship.rs/icon.png
image: https://starship.rs/icon.png
```

```zsh
brew install starship

curl -sS https://starship.rs/install.sh | sh
```

## Zsh 

Add the following to the end of `~/.zshrc`:

```sh
# ~/.zshrc

eval "$(starship init zsh)"
```

## Nushell 

WARNING
This will change in the future. Only Nushell v0.78+ is supported.

Add the following to the end of your Nushell env file (find it by running `$nu.env-path` in Nushell):

```sh
mkdir ~/.cache/starship
starship init nu | save -f ~/.cache/starship/init.nu
```

And add the following to the end of your Nushell configuration (find it by running `$nu.config-path`):

```sh
use ~/.cache/starship/init.nu
```

## Using starship in VSCode terminal

### starship fonts not showing correctly in integrated terminal

```
mkdir -p ~/.local/share/fonts
ln -s ~/.local/share/fonts/
~/.fonts 
cd ~/.fonts 
curl -OL https://github.com/ryanoasis/nerd-fonts/releases/latest/download/Hack.tar.xz 
tar -xvf Hack.tar.xz
```

Add to settings `"terminal.integrated.fontFamily": "Hack Nerd Font",`