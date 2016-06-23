Various vscode tasks files
==========================

This is a list of [vscode]() `tasks.json` files to automate some simple commands, mainly
builds, tests, etc.

Pandoc
------
``` json
{
    "version": "0.1.0",
    "command": "pandoc",
    "isShellCommand": true,
    "showOutput": "silent",
    "tasks": [
        {
            "taskName": "build html",
            "args": ["-s", "--mathjax","-o", "${fileBasename}.html", "${file}"],
            "isBuildCommand": true,
            "suppressTaskName": true                   
        },
        {
            "taskName": "build pdf",
            "args": ["-o", "${fileBasename}.pdf", "${file}"],
            "isTestCommand": true, 
            "suppressTaskName": true          
        }
    ]

}
```

Nim
---
``` json
{
    "version": "0.1.0",
    "command": "nim",
    "isShellCommand": true,
    "showOutput": "always",
    "tasks": [
        {
            "taskName": "run build",
            "args": ["c","-r","project.nim"],
            "isBuildCommand": true,
            "suppressTaskName": true                   
        },
        {
            "taskName": "run tests",
            "args": ["c", "-r","tests/project.nim"],
            "isTestCommand": true, 
            "suppressTaskName": true          
        },
        {
            "taskName": "run file",
            "args": ["c","-d:openblas","-r","${file}"], 
            "suppressTaskName": true          
        }
    ]

}
```

You can add `"-d:DefineSmth"` to `arg` to pass a definition, eg:
`"-d:openblas"` defines openblas, for example when using `linalg`