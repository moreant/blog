---
title: 'Ubuntu 安装最新版 nodejs'
date: 2023-03-26T13:40:14+08:00
slug: 'ubuntu-install-latest-nodejs'
image: ubuntu-install-latest-nodejs.webp
categories:
  - memory
tag:
  - Ubuntu
  - Nodejs
---

## 卸载旧版本

在 Ubuntu 22.04，apt 默认的 nodejs 版本是 v12.22.9，而最新的 nodejs 都已经 v18.13.0 了

卸载之前安装的旧版 nodejs

```bash
sudo apt remove nodejs
```

确认已经卸载完成

```bash
node -v
# zsh: command not found: node
```

清理旧版本依赖

```bash
sudo apt autoremove
```

## 安装新版本

设置新版的依赖地址

如果想安装其他版本，可以将 setup_18 修改为 setup_16

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```

安装 nodejs

```bash
sudo apt-get install -y nodejs
```

检查版本

```bash
node -v
# v18.13.0
```

建议顺手开启包管理配置

