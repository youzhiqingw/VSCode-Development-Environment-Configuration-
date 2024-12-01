# VSCode C/C++ 开发环境配置指南

#### 介绍

这是一个介绍如何在 Visual Studio Code (VS Code) 中配置和开发 C 语言项目的仓库

本指南旨在帮助你在 Visual Studio Code (VS Code) 中快速配置并优化 C/C++ 开发环境。

## 目录

1. [安装 VS Code](#安装-vs-code)
2. [安装 C/C++ 编译器](#安装-cc-编译器)
3. [安装 VS Code 扩展](#安装-vs-code-扩展)
4. [配置 `.vscode` 文件夹](#配置-vscode-文件夹)
   - [`c_cpp_properties.json`](#c_cpp_propertiesjson)
   - [`tasks.json`](#tasksjson)
   - [`launch.json`](#launchjson)
   - [`settings.json`](#settingsjson)
5. [创建和运行 C/C++ 项目](#创建和运行-cc-项目)
6. [调试 C/C++ 代码](#调试-cc-代码)

## 安装 VS Code

首先，从 [VS Code 官方网站](https://code.visualstudio.com/) 下载并安装 Visual Studio Code。

## 安装 C/C++ 编译器

- 使用 [MinGW](https://www.mingw-w64.org/)（Minimalist GNU for Windows）作为 GCC 编译器的 Windows 端口。

## 安装 VS Code 扩展

要优化你的开发体验，安装以下 VS Code 扩展：

- **C/C++**：由 Microsoft 提供，提供 C/C++ 语言支持，包括 IntelliSense、调试和代码浏览功能。
- **CMake Tools**：提供 CMake 项目管理和构建支持，可以轻松配置和管理 CMake 项目。
- **C/C++ Themes**：提供多种适用于 C/C++ 开发的代码主题，使代码更易阅读和美观。
- **CMake**：支持 CMake 配置文件和语法，增强 CMake 项目的支持。
- **JetBrains Icon Theme**：一个流行的图标主题，可以美化你的 VS Code 界面，提供多种图标样式以便于区分文件类型。

## 配置 `.vscode` 文件夹

在你的 C/C++ 项目文件夹中创建一个名为 `.vscode` 的文件夹，并在其中添加以下文件：

### `c_cpp_properties.json`

配置编译器路径、包含路径、定义宏等。配置示例如下：

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

定义编译任务。以下示例展示了如何使用 GCC 编译器构建项目：

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

配置调试器。以下是针对 C 程序的调试配置示例：

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
            "miDebuggerPath": "C:/MinGW/bin/gdb.exe" // 请根据实际情况调整路径
        }
    ]
}
```

### `settings.json`

在 VS Code 的全局或工作区 `settings.json` 文件中配置与 C/C++ 相关的设置。例如，可以设置为自动格式化代码，或配置调试器等。

## 创建和运行 C/C++ 项目

1. 创建一个新的 C/C++ 文件，例如 `main.c`，并编写你的 C/C++ 代码。
2. 使用 VS Code 的任务运行器（按 `Ctrl+Shift+B`）来编译你的代码。
3. 如果配置正确，编译后的可执行文件将出现在你的项目文件夹中，你可以直接在 VS Code 的终端中运行它。

## 调试 C/C++ 代码

1. 在你的代码中设置断点。
2. 使用 VS Code 的调试面板（或按 F5）来启动调试器。
3. 你可以逐步执行代码、查看变量值、检查内存等，帮助你更有效地诊断和修复问题。

通过以上步骤，你就可以在 VS Code 中配置一个完整的 C/C++ 开发环境。
