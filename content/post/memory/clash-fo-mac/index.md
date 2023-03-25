---
title: 'Clash for Windows 在 macOS 安装后无法打开，提示损坏'
date: 2021-08-14T04:02:21+08:00
slug: 'clash-fo-mac'
description: sudo xattr -r -d com.apple.quarantine /Applications/Clash\ for\ Windows.app
image: not-open.webp
tags:
  - Mac
categories:
  - memory
---

网络下载应用被 Apple 添加隔离标识，终端执行以下命令解除即可：

```zsh
sudo xattr -r -d com.apple.quarantine /Applications/Clash\ for\ Windows.app
```

附上完整文档地址：  
https://docs.cfw.lbyczf.com/contents/questions.html
