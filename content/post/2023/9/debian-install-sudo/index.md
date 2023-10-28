---
title: 'Debian 安装 sudo'
date: '2023-09-11T00:52:00+08:00'
slug: 'debian-install-sudo'
description: '不是很懂为啥 Debian12 居然连 sudo 都没预装'
image: debian-install-sudo.webp
tags:
  - Debian
categories:
  - memory
---

## 步骤
1. 切换到 root 用户，需要输入 root 用户的密码
```bash
su --login
```

2. 安装 sudo
```bash
apt install sudo
```

3. 添加 jhon-smith 用户到 sudo 用户组，**此处需要将 jhon-smith 替换为你的用户名**
```bash
adduser jhon-smith sudo
```

## 参考资料
> [sudo - Debian Wiki](https://wiki.debian.org/sudo)