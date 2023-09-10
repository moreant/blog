---
title: 'Docker 安装 PostgreSQL'
date: '2023-07-16T16:27:00+08:00'
slug: 'docker-install-postgresql'
description: '以 Ubuntu 为例'
image: docker-install-postgresql.webp
tags:
  - Docker
  - PostgreSQL
categories:
  - memory
---

## 1. 拉取镜像

由于国内 Docker 的镜像源经常出现 latest tag 与官方源的 latest 不是同一个版本的情况，所以最好指定版本号拉取镜像。

```bash
docker pull postgres:15.3
```

## 2. 创建容器

```bash
docker run -itd \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=dataPassword \
-p 5432:5432 \
-v /app/postgresql:/var/lib/postgresql/data \
--name postgresql postgres:15.3
```

参数说明:  
| 参数 | 说明 |  
| --- | --- |  
| POSTGRES_USER=postgres | 设置 postgres 用户的 |
| POSTGRES_PASSWORD=dataPassword | 设置 postgres 用户的密码 |  
| /var/lib/postgresql/data | 容器中 PostgreSQL 数据库的存储路径 |  
