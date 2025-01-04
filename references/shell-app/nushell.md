---
creation date: 2024-11-04 13:45
modification date: Monday, 4th November 2024, 13:45:47
tags:
  - shell
command: nu
description: Shell alternative
os:
  - linux
  - macos
source: brew
url: https://www.nushell.sh
---
---
```cardlink
url: https://www.nushell.sh
title: "Nushell"
description: "A new type of shell."
host: www.nushell.sh
favicon: https://www.nushell.sh/icon.png
```

## references

```cardlink
url: https://github.com/nushell/awesome-nu
title: "GitHub - nushell/awesome-nu: A curated list of awesome tools that work within the nu language ecosystem e.g. nushell, scripts, nana, etc."
description: "A curated list of awesome tools that work within the nu language ecosystem e.g. nushell, scripts, nana, etc. - nushell/awesome-nu"
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://opengraph.githubassets.com/858183f70c71b65f8a62d2ac523575148945309eca6edf5cd0764c1b1dc12921/nushell/awesome-nu
```


```cardlink
url: https://www.youtube.com/watch?v=uJsZATwQ3R8&t=860s
title: "Is Nushell Worth The Hype?"
description: "This video is sponsored by Auth0!Up to 25k users can authenticate your app for free, get started here: https://auth0.com/signup?utm_source=devopstoolbox&utm_..."
host: www.youtube.com
favicon: https://www.youtube.com/s/desktop/3637873e/img/logos/favicon_32x32.png
image: https://i.ytimg.com/vi/uJsZATwQ3R8/maxresdefault.jpg
```



```cardlink
url: https://www.youtube.com/watch?v=LFBOLx5KiME
title: "I Was Wrong About Nushell (I Finally Get It Now)"
description: "✅ Zero To KNOWING Kubernetes in Under 90 Minutes:https://learn.omerxx.com/courses/k8s-from-scratch✅ Build a Second Brain With Neovim in Under 90 Minutes: htt..."
host: www.youtube.com
favicon: https://www.youtube.com/s/desktop/3637873e/img/logos/favicon_32x32.png
image: https://i.ytimg.com/vi/LFBOLx5KiME/maxresdefault.jpg
```
	

---
## using vim by default

```
# At the bottom $nu.env-path 
# Will allow you to use config env or config nu
$env.EDITOR = "nvim"
```

```
# Choose vi for vi cli mode in $nu.config-path
edit_mode: vi
```

## running system command like open

### [Escaping to the System](https://www.nushell.sh/book/escaping.html#escaping-to-the-system)

Nu provides a set of commands that you can use across different OSes ("internal" commands), and having this consistency is helpful. Sometimes, though, you want to run an external command that has the same name as an internal Nu command. To run the external [`ls`](https://www.nushell.sh/commands/docs/ls.html) or [`date`](https://www.nushell.sh/commands/docs/date.html) command, for example, you use the caret (^) command. Escaping with the caret prefix calls the command that's in the user's PATH (e.g. `/bin/ls` instead of Nu's internal [`ls`](https://www.nushell.sh/commands/docs/ls.html) command).

Nu internal command:

```
> ls
```

Escape to external command:

```
> ^ls
```

Open the finder window:

```
> ^open .

#or define an alias
> : alias open = ^open
> open .
```

### [Windows Note](https://www.nushell.sh/book/escaping.html#windows-note)

When running an external command on Windows, nushell [used to](https://www.nushell.sh/blog/2022-08-16-nushell-0_67.html#windows-cmd-exe-changes-rgwood) use [Cmd.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/cmd) to run the command, as a number of common commands on Windows are actually shell builtins and not available as separate executables. [Coming from CMD.EXE](https://www.nushell.sh/book/coming_from_cmd.html) contains a list of these commands and how to map them to nushell native concepts.