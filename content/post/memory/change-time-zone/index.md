---
title: '修改 Linux 中的时区'
slug: 'change-time-zone'
date: 2024-02-26T16:16:00+08:00
description: 避免 date 的时间看起来怪怪的
tags:
  - Linux
  - Ubuntu
  - Debian
categories:
  - memory
---

## 替换 localtime
```bash
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

## 修改时区

`/etc/timezone` 文件修改为。

```bash
Asia/Shanghai
```
