Various vscode tasks files
==========================

This is a list of [vscode]() `tasks.json` files to automate some simple commands, mainly
builds, tests, etc. without having to write extensions.

## Table of Contents

- [Pandoc](#Pandoc)
- [Nim](#Nim)
- [Julia](#Julia)
- [Octave](#Octave)
- [Flow](#Flow)

---

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

You can add `"-d:<something>"` to `args` to pass a definition, eg:
`"-d:openblas"` defines openblas, for example when using `linalg`.
Or simply create a `nim.cfg` file and put `define: <something>` inside.

Julia
-----

```json
{
    "version": "0.1.0",
    "command": "julia",
    "isShellCommand": true,
    "showOutput": "always",
    "tasks": [
        {
            "taskName": "run file",
            "args": ["--precompiled=yes", "${file}"],
            "isBuildCommand": true,
            "suppressTaskName": true                   
        },
    ]

}
```
Octave
------

**Note**: needs `octave-cli` in `PATH`

``` json
{
    "version": "0.1.0",
    "command": "octave-cli",
    "isShellCommand": true,
    "args": ["${file}"],
    "isBuildCommand": true,
    "suppressTaskName": true,
    "showOutput": "always"
}
```
Flow
----

Flow is a build tool for haxe, mainly used by snowkit projects.
**Note**: Defaults to building the `web` target.

``` json
{
    "version": "0.1.0",
    "command": "flow",
    "isShellCommand": true,
    "showOutput": "always",
    "tasks": [
        {
            "taskName": "run windows",
            "args": ["run","windows"],
            "suppressTaskName": true                   
        },
        {
            "taskName": "run web",
            "args": ["run","web"], 
            "isBuildCommand": true,
            "suppressTaskName": true          
        }
    ]

}

