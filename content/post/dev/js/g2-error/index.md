---
title: 'g2 报错'
date: 2022-11-13T19:02:21+08:00
slug: 'g2-error'
description: '--no-module'
image: g2-err.png
tags:
  - JavaScript
  - Vue
categories:
  - memory
---

G2 + Webpack5 本地开发无问题，打包后无限卡 Loading

Uncaught TypeError: Cannot assign to read only property 'constructor' of object '#\<Group>'

构建时加上 --no-module 解决

> 参考
> https://github.com/nklayman/vue-cli-plugin-electron-builder/issues/1089
