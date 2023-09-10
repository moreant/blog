---
title: 'Docker 迁移数据卷'
date: '2023-07-16T01:41:00+08:00'
slug: 'docker-move-volume'
description: '以迁移 uptim-kume 容器为例，记录备份和迁移 Docker 数据卷的过程'
image: docker-move-volume.webp
tags:
  - Docker
categories:
  - memory
---

## 备份
首先，我们需要知道 uptime-kume 的数据存放位置，通过官方文档可以知道是在 `/app/data`

因此可以使用以下指令进行备份:
```bash
docker run --rm \
--volumes-from uptime-kuma \
-v $(pwd):/backup \
alpine \
tar cvf /backup/backup.tar /app/data/
```

参数说明:  
|参数|说明|  
|--|--|  
|`--rm`|容器退出后自动删除容器|  
|`--volumes-from uptime-kuma`|挂载 uptime-kuma 容器的数据卷|  
|`-v $(pwd):/backup`|挂载当前目录到容器的 `/backup` 目录|  
|`alpine`|使用 alpine 镜像|  
|`tar cvf /backup/backup.tar /app/data/`|在容器中执行 `tar cvf /backup/backup.tar /app/data/` 命令|

执行后应该会在当前目录中多出一个 `backup.tar` 文件，这个文件就是我们的数据卷备份文件。 


## 移动
使用 `scp` 命令将备份文件传输到目标服务器上。
```bash
scp backup.tar user@172.16.111.50:~/
```

## 恢复
首先保证目标服务器上已经运行了 uptime-kuma 容器，然后使用以下指令进行恢复:
```bash
docker run --rm \
--volumes-from uptime-kuma \
-v $(pwd):/backup \
alpine \
tar xvf /backup/backup.tar
```

因为压缩时带了绝对路径，所以不需要 -C 来指定解压路径。

## 参考资料
> - [🎯 备份和迁移数据 - Docker 快速入门 - 易文档](https://docker.easydoc.net/doc/81170005/cCewZWoN/XQEqNjiu)  
> - [备份 Docker 镜像容器和数据以及无痛迁移 | Verne in GitHub](https://einverne.github.io/post/2018/03/docker-related-backup.html)  
