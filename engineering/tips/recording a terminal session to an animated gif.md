---
creation date: 2025-14-02 12:12:12
tags:
  - dev/documentation
  - shell/cli
---
---
## pre-requisites
```bash
brew install asciinema
brew install agg
```

## creating an animated gif
```bash
asciinema rec

# everything you do is now recorded.
# when finish, hit <ctrl+d>
# when prompted to save, type s.

# to convert to gif
agg <recordedfile>.cast animsession.gif

# to use fancy fonts (if you have some in your prompt)
 agg --font-family "JetBrainsMonoNL Nerd Font"  test.cast test.gif
 
```