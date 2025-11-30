
## cli tool

```dataviewjs
// Render a simple table of book info sorted by rating.
const table = dv.markdownTable(["cli", "command", "desc"], dv.pages("#shell/cli")
    .sort(b => b.file.link)
    .map(b => [b.file.link, b.command, b.description]))

dv.paragraph(table);
```


[carapace](02-subjects/tools-and-utilities/shell/carapace.md) 
A multi-shell completion **[library](https://github.com/carapace-sh/carapace)** and **[binary](https://github.com/carapace-sh/carapace-bin)**.  Very powerful.

[m-cli](02-subjects/tools-and-utilities/cli/m-cli.md)
Mac configuration/control swiss army knife

[zoxide](02-subjects/tools-and-utilities/cli/zoxide.md)
Better CD navigation.  Remembers where you've bin, making it quicker to get back to where you've been in the past.

```dataviewjs
// Render a simple table of book info sorted by rating.
const table = dv.markdownTable(["cli", "os", "command", "desc"], dv.pages("#computer/cli")
    .sort(b => b.file.link)
    .map(b => [b.file.link, b.os, b.command, b.desc]))

dv.paragraph(table);
```


## cli process monitor 

```dataviewjs
// Render a simple table of book info sorted by rating.
const table = dv.markdownTable(["cli", "os", "command", "desc"], dv.pages("#computer/sys-mon")
    .sort(b => b.file.link)
    .map(b => [b.file.link, b.os, b.command, b.desc]))

dv.paragraph(table);
```

```dataviewjs
// Render a simple table of book info sorted by rating.
const table = dv.markdownTable(["cli", "os", "command", "desc"], dv.pages("#shell/system-monitor")
    .sort(b => b.file.link)
    .map(b => [b.file.link, b.os, b.command, b.description]))

dv.paragraph(table);
```

```dataviewjs
// Render a simple table of book info sorted by rating.
const table = dv.markdownTable(["cli", "os", "command", "desc"], dv.pages("#dev/language/python")
    .sort(b => b.file.link)
    .map(b => [b.file.link, b.os, b.command, b.description]))

dv.paragraph(table);
```


```dataviewjs const tCount = dv.pages("") .file.tasks.filter(task => dv.func.contains(task.tags, "⛑️") && !task.completed) .length; ```
## ide
[vscode](02-subjects/tools-and-utilities/desktop/vscode.md)

## language/compilers/toolchains
[python](04-archive/newvault/engineering/language/python.md)
[esp-idf](02-subjects/tools-and-utilities/sdks/esp-idf.md) - espressif (ESP32) toolchain

## package managements
[homebrew](02-subjects/tools-and-utilities/cli/homebrew.md)
Using it over nix-os.  Nix os is much more powerful but requires sudo access, which I do not have on my company macbook

## prompts
[starship](02-subjects/tools-and-utilities/shell/starship.md)
Very fast prompt.  Comparable to power10k

## shell
[nushell](02-subjects/tools-and-utilities/cli/nushell.md)
A new type of shell.  Really nice, but is very different from zsh/bash.  Currently investigating to get a feel on how I could use it.

## software
[obsidian](02-subjects/tools-and-utilities/desktop/obsidian.md) -- knowledge management
## system configurations
[mac-system-settings](04-archive/newvault/os/macos/mac-system-settings.md)
[m-cli](02-subjects/tools-and-utilities/cli/m-cli.md)

## gui
```dataviewjs
// Render a simple table of book info sorted by rating.
const table = dv.markdownTable(["cli", "languages", "command", "desc"], dv.pages("#dev/gui")
    .sort(b => b.file.link)
    .map(b => [b.file.link, b.tags, b.command, b.description]))

dv.paragraph(table);
```


