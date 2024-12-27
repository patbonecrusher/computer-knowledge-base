---
creation date: 2024-11-04 13:52
modification date: Monday, 4th November 2024, 13:52:12
tags:
  - dev/language/python
---
## Using [uv](uv.md)


## Using [asdf](asdf.md)
Before installing python using asdf, install the following dependencies

### MacOS
```shell
# os/macos
brew install ncurses
brew install readline
brew install openssl sqlite3 xz zlib
brew install python-tk

export LDFLAGS="-L/opt/homebrew/opt/zlib/lib"
export CPPFLAGS="-I/opt/homebrew/opt/zlib/include"
```
### Linux 
```shell
sudo apt install libncurses-dev libreadline-dev libssl-dev libbz2-dev libsqlite3-dev lzma python3-tk

sudo apt-get install libffi-dev
sudo apt-get install lzma
sudo apt-get install liblzma-dev
sudo apt-get install libbz2-dev
sudo apt install tk-dev
```

```shell
asdf plugin-add python
```

## nushell
To use venv
```sh
# source is not a valid command in nushell
overlay use .venv/bin/activate.nu
```

---
#### references

```cardlink
url: https://medium.com/python-in-plain-english/10-python-features-that-seem-confusing-but-are-actually-brilliant-2197989729bd
title: "10 Python Features That Seem Confusing (But Are Actually Brilliant)"
description: "Python features that seem hard but are mind-blowing once you get them. Ready to master the magic? Let’s go!"
host: medium.com
favicon: https://miro.medium.com/v2/resize:fill:256:256/1*D3hZzYqqsM6-wef-5zzDIA.png
image: https://miro.medium.com/v2/resize:fit:1080/1*ztrJKdy2_d_60lr7MCvEgA.png
```

```cardlink
url: https://medium.com/pythoneers/40-python-one-liners-you-must-try-ae4d3e4d2e5f
title: "40 Python One-Liners You Must Try"
description: "Why Code More, When You Can Do It In One Line ??"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/da:true/resize:fit:1000/0*Unsw-UEB5KSLNg_n
```

```cardlink
url: https://medium.com/ai-simplified-in-plain-english/enter-2025-with-these-5-cool-python-libraries-9169b581efb1
title: "Enter 2025 with these 5 Cool Python Libraries"
description: "Hey there!"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/resize:fit:1200/1*wdpcgEKYInz2FNoHWfwOqw.png
```

