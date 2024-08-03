---
title: '设置 Linux 的时区为北京时间'
slug: 'set-time-zone-in-linux'
image: set-time-zone-in-linux.webp
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
sudo cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

## 修改时区

将 `/etc/timezone` 文件的内容修改为 `Asia/Shanghai`。

```bash
echo "Asia/Shanghai" | sudo tee /etc/timezone
```
