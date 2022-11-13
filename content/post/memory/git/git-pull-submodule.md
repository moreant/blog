---
title: 'git 拉取子模块'
date: 2022-11-13T16:42:20+08:00
slug: 'git-pull-submodule'
description: 'git submodule update --init --recursive'
tags:
  - git
categories:
  - memory
---

1. 首次拉取的时候可以加上 `--recursive` 参数

```bash
git clone --recursive 仓库地址
```

2. 如果已经将仓库克隆到本地了，想拉子模块

```bash
git submodule update --init --recursive
```

3. 更新子模块

```bash
git submodule update --recursive
```
