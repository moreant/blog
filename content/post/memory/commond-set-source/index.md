---
title: '使用命令设置清华源'
slug: 'commond-set-source'
date: 2024-02-26T15:58:00+08:00
description: 在 Docker 里想要设置源，连个 Vim 都没有，所以只能用命令行设置了。
tags:
  - Ubuntu
  - Debian
categories:
  - memory
---

可以复制头尾，然后中间的参考清华源的指南进行修改。  
https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

## Ubuntu 22.4

```bash
tee /etc/apt/sources.list <<-'EOF'
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
EOF
```

## Debian 11

```bash
tee /etc/apt/sources.list <<-'EOF'
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
deb https://security.debian.org/debian-security bullseye-security main contrib non-free
EOF
```

## Debian 12
```bash
tee /etc/apt/sources.list <<-'EOF'
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm main contrib non-free non-free-firmware
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm-updates main contrib non-free non-free-firmware
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm-backports main contrib non-free non-free-firmware
deb https://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
EOF
```