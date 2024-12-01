# VSCode C/C++ Development Environment Configuration Guide

#### Introduction
This is a repository that introduces how to configure and develop C language projects in Visual Studio Code (VS Code).

This guide aims to help you quickly configure and optimize your C/C++ development environment in Visual Studio Code (VS Code).

## Table of Contents

1. [Installing VS Code](#installing-vs-code)
2. [Installing C/C++ Compiler](#installing-cc-compiler)
3. [Installing VS Code Extensions](#installing-vs-code-extensions)
4. [Configuring the `.vscode` Folder](#configuring-the-vscode-folder)
   - [`c_cpp_properties.json`](#c_cpp_propertiesjson)
   - [`tasks.json`](#tasksjson)
   - [`launch.json`](#launchjson)
   - [`settings.json`](#settingsjson)
5. [Creating and Running C/C++ Projects](#creating-and-running-cc-projects)
6. [Debugging C/C++ Code](#debugging-cc-code)

## Installing VS Code

First, download and install Visual Studio Code from the [VS Code official website](https://code.visualstudio.com/).

## Installing C/C++ Compiler

- Use [MinGW](https://www.mingw-w64.org/) (Minimalist GNU for Windows) as a Windows port of the GCC compiler.


## Installing VS Code Extensions

To optimize your development experience, install the following VS Code extensions:

- **C/C++**: Provided by Microsoft, offers C/C++ language support, including IntelliSense, debugging, and code browsing features.
- **CMake Tools**: Provides CMake project management and build support, allowing easy configuration and management of CMake projects.
- **C/C++ Themes**: Offers various code themes suitable for C/C++ development, making code easier to read and visually appealing.
- **CMake**: Supports CMake configuration files and syntax, enhancing support for CMake projects.
- **JetBrains Icon Theme**: A popular icon theme that can beautify your VS Code interface, offering various icon styles to differentiate file types.

## Configuring the `.vscode` Folder

Create a folder named `.vscode` in your C/C++ project folder and add the following files to it:

### `c_cpp_properties.json`

Configure compiler paths, include paths, defined macros, etc. An example configuration is as follows:

```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [],
            "compilerPath": "C:/MinGW/bin/gcc.exe",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "gcc-x86"
        }
    ],
    "version": 4
}
```

### `tasks.json`

Define build tasks. The following example demonstrates how to build a project using the GCC compiler:

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "command": "gcc",
            "args": [
                "-g",
                "main.c",
                "-o",
                "main.exe"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": ["$gcc"],
            "detail": "Generated task by C/C++ Extension."
        }
    ]
}
```

### `launch.json`

Configure the debugger. The following is an example debug configuration for C programs:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug C Program",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/main.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "build",
            "miDebuggerPath": "C:/MinGW/bin/gdb.exe" // Adjust the path as needed
        }
    ]
}
```

### `settings.json`

Configure C/C++-related settings in VS Code's global or workspace `settings.json` file. For example, you can set automatic code formatting or configure the debugger.

## Creating and Running C/C++ Projects

1. Create a new C/C++ file, such as `main.c`, and write your C/C++ code.
2. Use VS Code's task runner (press `Ctrl+Shift+B`) to compile your code.
3. If configured correctly, the compiled executable will appear in your project folder, and you can run it directly in VS Code's terminal.

## Debugging C/C++ Code

1. Set breakpoints in your code.
2. Use VS Code's debug panel (or press F5) to start the debugger.
3. You can step through the code, view variable values, inspect memory, etc., helping you diagnose and fix issues more effectively.

By following these steps, you can configure a complete C/C++ development environment in VS Code.