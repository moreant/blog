---
title: 'Npm 换源'
slug: 'npm-change-registry-source'
date: 2021-08-14T01:53:02+08:00
description: 不啰嗦 npm config set registry https://registry.npmmirror.com
tags:
  - JavaScript
categories:
  - memory
---

鉴于网上内容大部分过于啰嗦，故自己记录一下

## 查看当前源

```bash
npm config get registry
```

## 淘宝源

1. 本项目使用

```bash
npm install --registry=https://registry.npmmirror.com
```

2. 全局使用

```bash
npm config set registry https://registry.npmmirror.com
```

<br><br>

## 官方源

1. 本项目使用

```bash
npm install --registry=https://registry.npmjs.org/
```

2. 全局使用

```bash
npm config set registry https://registry.npmjs.org/
```
