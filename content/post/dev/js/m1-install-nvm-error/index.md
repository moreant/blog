---
title: "m1 nvm 安装 node 异常"
date: 2021-08-27T23:51:45+08:00
slug: "m1-install-nvm-error"
description: "clang: error: no such file or directory: 'CXX=c++'"
image: terminal-error.png
tags: 
    - JavaScript
    - Mac
categories:
    - dev
---
## 问题描述
![控制台报错](terminal-error.webp)

## 解决方法
需要先执行以下指令再进行安装  
```
arch -x86_64 zsh
```  
应该是因为 v14 及以前的版本不支持 arm 版本的处理器，所以需要使用 Rosetta 2 来进行安装。
## 参考资料  
> [mac M1 nvm 安装问题_CSDN](https://blog.csdn.net/longgege001/article/details/114067242)   
> [nvm install node fails to install on macOS Big Sur M1 Chip](https://github.com/nvm-sh/nvm/issues/2350#issuecomment-734132550)
