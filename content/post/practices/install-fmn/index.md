---
title: '安装 Fast Node Manager (fnm) 以管理 Nodejs 版本'
date: '2023-04-22T21:40:00+08:00'
slug: 'use-fnm'
description: '自动切换版本，nvm 的最佳替代品。'
image: use-fnm.webp
tags:
  - Nodejs
categories:
  - practices
---

## 前言
提到管理 Nodejs 版本，就不得不提到大名鼎鼎的 nvm 了，但是 nvm 有一个致命的缺点，就是它的自动切换版本极其麻烦，而 fnm 就没这个问题。并且 Windows 上的 [nvm](https://github.com/nvm-sh/nvm) 与 macOS 上的 [nvm](https://github.com/coreybutler/nvm-windows) 实际上并不是同一个，Windows 的只是借了 nvm 的名称，API略有不同，构建两者的语言更是完全不相同。而 fnm 在三大系统上都是同一个，这保证了 API 的一致性。


## 什么是 fnm
fnm 目前在 Github 上有 11.6k 的 star，是一个用 Rust 写的 Nodejs 版本管理工具。只需要在终端中简单的设置自动切换的脚本，并在项目中添加一个 `.node-version` 文件，就可以自动切换 Nodejs 版本了。

## 安装
### macOS/Linux
```bash
curl -fsSL https://fnm.vercel.app/install | bash
```

### Windows
```bash
scoop install fnm
```
## 配置
在使用前还需要根据终端的不同，进行一些配置。以下是支持并推荐的终端
- `bash`
- `zsh`
- `fish`
- `powershell`

### bash
在 bash 的配置文件 `~/.bashrc` 中添加以下内容
```bash
eval "$(fnm env --use-on-cd)"
```

### zsh
在 zsh 的配置文件 `~/.zshrc` 中添加以下内容
```bash
eval "$(fnm env --use-on-cd)"
```

### fish
创建一个 fish 的配置文件 `~/.config/fish/config.fish`，并添加以下内容
```bash
fnm env --use-on-cd | source
```

### powershell
将以下内容添加至 powershell 的配置文件 `~\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1` 或 `$PROFILE`中
```bash
fnm env --use-on-cd | Out-String | Invoke-Expression
```


## 使用
### 使用帮助
```bash
fnm help
```

### 安装 18 与 16 版本
```bash
fnm install 18
fnm install 16
```

### 指定 18 为默认版本
```bash
fnm default 18
```

### 设置自动切换的目标版本

```bash
# 检查当前版本
node --version
# 切换到 16 版本
fnm use v16.20.0
# 将当前版本保存到 .node-version 文件中
node --version > .node-version
```
当从其他目录切换到当前目录时，会自动切换到 16 版本，并输出 `Using Node v16.20.0`。

至此，fnm 的安装与使用就完成了。

