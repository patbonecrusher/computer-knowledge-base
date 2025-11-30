---
creation date: 05/17/2025
---
---

```json
{
    "env": {
        "myIncludePath": [],
        "myDefines": [
            "DEBUG",
            "MY_FEATURE=1"
        ],
        "espIdfPath": "/Users/pat/.tools/espidf/esp-idf-v541"
    },
    "configurations": [
        {
            "compileCommands": "${workspaceFolder}/build/sg1/compile_commands.json",
            "name": "sg1",
            "forcedInclude": [
                "${workspaceFolder}/build/sg1/config/sdkconfig.h"
            ],
            "includePath": [
                "${workspaceFolder}/**",
                "${workspaceFolder}/build/sg1/config",
                "${espIdfPath}/components/**"
            ],
            "browse": {
                "path": [
                    "${workspaceFolder}/**",
                    "${workspaceFolder}/build/sg1/config",
                    "${espIdfPath}/components/**"
                ],
                "limitSymbolsToIncludedHeaders": true,
                "databaseFilename": ""
            }, 
            "defines": [
                "__XTENSA__",
                "LOG_ENABLED"
            ],
            "macFrameworkPath": [
                "/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/System/Library/Frameworks"
            ],
            "compilerPath": "/usr/bin/clang",
            "cStandard": "c17",
            "cppStandard": "gnu++20",
            "intelliSenseMode": "macos-clang-x64"
        }
    ],
    "version": 4
}
```

```json
"C_Cpp.intelliSenseEngine": "Tag Parser"
```