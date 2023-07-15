---
title: 'Git 初始化配置'
date: '2023-06-12T15:40:00+08:00'
slug: 'git-init-config'
description: '最佳实践的 Git 初始化配置推荐'
image: git-init-config.webp
tags:
  - Git
categories:
  - practices
---

如果你是在 Windows 操作系统中使用 Git,可能会遇到乱码问题，可以参考我的另一篇博文 [Git 乱码问题](/p/fix-chinese-character-gibberish-in-git-bash/) 解决。


## 1. 设置大小写敏感
在 Windows 中，Git 默认是不区分大小写的。在重命名文件时容易发生血案。所以在 Windows 中，最好设置大小写敏感。

```bash
git config --global core.ignorecase false
```

## 2. 提交文件的换行符统一使用 LF
任然是 Windows 系统的的推荐配置，Windows 默认的换行符是 `CRLF`，而在 Linux 和 macOS 中是 `LF`。所以在 Windows 中，最好设置提交文件的换行符统一使用 LF`。

```bash
# 自动转换
git config --global core.autocrlf input
# 不符时输出警告
git config --global core.safecrlf warn
```

## 3. Git Pull 默认使用 rebase
Git Pull 默认使用 rebase，这样可以避免在合并分支时产生无用的 merge commit。

```bash
git config --global pull.rebase true
```

## 4. 设置 Git log 中的日期格式
Git log 中的日期格式默认是 `Wed May 17 10:58:19` 这种的，不太好看，可以设置成 `2023-05-17 10:58:19` 这种更符合中国宝宝体质的日期格式。

```bash
git config --global log.date iso
```

## 5. 解决 TLS certificate... 警告

```bash
git config --global http.sslVerify true
```

## 6. 记住网络认证
这样可以避免 GitLab 需要重复输入用户名和密码的问题。

```bash
git config --global credential.helper store
```

## 参考资料
> [【Git系列】Git 大小写不敏感引发的血案 - 掘金](https://juejin.cn/post/6979105615541075999)  
> [Git 多平台换行符问题(LF or CRLF)](https://blog.konghy.cn/2017/03/19/git-lf-or-crlf/)  
> [TLS certificate verification has been disabled!_我在村口看一只猫追一条狗的博客-CSDN博客](https://blog.csdn.net/xxwwh/article/details/119841089)

