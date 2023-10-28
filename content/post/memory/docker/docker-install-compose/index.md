---
title: 'Docker 安装 Compose'
date: '2023-09-11T00:08:00+08:00'
slug: 'docker-install-compose'
description: '不知道为啥官方文档介绍的这么乱'
image: docker-install-compose.webp
tags:
  - Docker
categories:
  - memory
---

尝试过全局安装，但是并没有成功，最后还是仅本用户安装了。

## 安装

1. 创建目录

```bash
mkdir -p ~/.docker/cli-plugins
```

2. 下载二进制文件

```bash
curl -L https://ghproxy.com/https://github.com/docker/compose/releases/latest/download/docker-compose-`uname -s`-`uname -m` > ~/.docker/cli-plugins/docker-compose
```

3. 添加可执行权限

```bash
chmod +x ~/.docker/cli-plugins/docker-compose
```

4. 测试是否安装成功

```bash
docker compose version
# Docker Compose version v2.21.0
```

## 参考资料

> [Linux 安装 docker compose v2](https://www.iszy.cc/posts/linux-install-docker-compose-v2/)  
> [docker/compose: Define and run multi-container applications with Docker](https://github.com/docker/compose)
