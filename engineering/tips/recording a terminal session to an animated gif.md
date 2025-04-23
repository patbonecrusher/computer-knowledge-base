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
```