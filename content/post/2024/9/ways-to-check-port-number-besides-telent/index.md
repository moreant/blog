---
title: '除了 telnet 还有哪些方法检查端口号'
slug: 'ways-to-check-port-number-besides-telent'
image: ways-to-check-port-number-besides-telent.webp
date: 2024-09-22T17:12:00+08:00
description: curl 和 ssh 都行
tags:
  - Linux
categories:
  - memory
---

## curl

```bash
curl -v 127.0.0.1:80
```

## ssh

```bash
ssh -v 127.0.0.1 -p 80
```

## echo
这个是用来检查本机端口是否开启的，不适用于远程端口。

```bash
echo > /dev/tcp/127.0.0.1/80
```
