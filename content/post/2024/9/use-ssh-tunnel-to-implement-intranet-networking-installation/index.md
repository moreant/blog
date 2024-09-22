---
title: '利用 ssh 隧道实现内网机器联网安装'
slug: 'use-ssh-tunnel-to-implement-intranet-networking-installation'
date: 2024-09-22T18:10:00+08:00
description: curl 和 ssh 都行
tags:
  - Linux
categories:
  - memory
---

## 前言
对于内网机器，APT 和 Git 如果能直接安装是比较方便的。这里就介绍一下如何利用 SSH 隧道实现内网联网安装。

首先假设 SSH 隧道将本机的 HTTP 代理端口到内网机器的 7890 端口了。

## APT
```bash
sudo apt install tmux -o Acquire::http::proxy="http://127.0.0.1:7890/" 
```

## Git
```bash
git clone https://github.com/gpakosz/.tmux.git -c "https.proxy=http://127.0.0.1:7890" -c "http.proxy=http://127.0.0.1:7890" 
```

## NPM

待补充。
