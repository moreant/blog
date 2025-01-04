---
title: 'Linux 快速初始化'
slug: 'linux-quick-init'
date: 2025-01-04T22:00:00+08:00
description: 基于 Debian 的 Linux 快速初始化
tags:
  - Linux
categories:
  - practice
---

## 到手一键

### SSH

SSH 密钥一键添加

```bash
bash <(curl -fsSL https://al.tptp.net/d/s/mobox/get-sh/key.sh) -u https://al.tptp.net/d/s/mobox/get-sh/aps.pub
```

> [SSH 密钥一键配置脚本 使用教程 - P3TERX ZONE](https://p3terx.com/archives/ssh-key-installer.html)

### 网络优化

一般用 BRP+FQ 即可

```bash
bash <(curl -fsSL https://git.io/kernel.sh)
```

> [jinwyp/one_click_script: install latest or LTS linux kernel and enable BBR or BBR plus](https://github.com/jinwyp/one_click_script)

## 基础软件

### APT

如果服务器在国内，推荐使用 chsrc 一键修改镜像源

```bash
curl https://chsrc.run/posix | sudo bash
```

> [RubyMetric/chsrc: chsrc 全平台通用换源工具与框架. Change Source everywhere for every software](https://github.com/RubyMetric/chsrc)

然后安装一些常用依赖

```bash
apt update
apt install -y curl tmux netcat-openbsd nmap ncdu \
htop telnet lsof unzip \
git lrzsz neovim jq ca-certificates
```

### 安装 Docker

如果不确定能否安装 Docker 可以用这个脚本检查。

```bash
curl -sSL https://github.com/moby/moby/raw/master/contrib/check-config.sh | bash
```

如果返回 404 则说明无法安装 Docker

```bash
curl -fsSL https://get.docker.com -o install-docker.sh
```

```bash
sudo sh install-docker.sh
```

## 脚本优化
### Bash 着色以及 rm 二次确认
直接编辑 ~/.bashrc , 解除若干注释即可

```bash
vim ~/.bashrc
```

## 非必装软件

### atuin

```bash
curl --proto '=https' --tlsv1.2 -LsSf https://setup.atuin.sh | sh
```

### Caddy

```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https curl
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy
```

### Dufs

[Dufs](https://github.com/sigoden/dufs/)

### Portainer

看需要。