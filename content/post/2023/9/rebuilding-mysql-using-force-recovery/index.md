---
title: '使用 Force Recovery 重建 MySQL 数据库'
date: '2023-09-16T23:51:00+08:00'
slug: 'rebuilding-mysql-using-force-recovery'
description: '服务器被强制断电这种事情太恐怖了'
image: rebuilding-mysql-using-force-recovery.webp
tags:
  - MySQL
categories:
  - dev
---

## 问题描述
周二一早到公司，发现服务器被强制断电了，有两个 MySQL 数据库遇到了无法启动的问题。然后翻阅 `/var/log/mysqld.log` 的 MySQL 日志发现了如下错误：

```log
2023-09-13T04:51:19.944175Z 0 [ERROR] InnoDB: Page [page id: space=0, page number=412] log sequence number 71278467353 is in the future! Current system log sequence number 44533092382.
2023-09-13T04:51:19.944179Z 0 [ERROR] InnoDB: Your database may be corrupt or you may have copied the InnoDB tablespace but not the InnoDB log files. Please refer to http://dev.mysql.com/doc/refman/5.7/en/forcing-innodb-recovery.html for information about forcing recovery.
```

## 解决步骤
### 1. 以 `force recovery` 模式启动 MySQL
先停止 MySQL 数据库
```bash
systemctl stop mysql
```

编辑 MySQL 配置文件
实际的配置文件的地址可能有所不同，本文的在 `/etc/mysql/mysql.conf.d/mysqld.cnf`
```bash
vim /etc/mysql/mysql.conf.d/mysqld.cnf
```

添加以下内容到文件底部
```bash
innodb_force_recovery=6
```
启动 MySQL
```bash
systemctl start mysql
```

此时 MySQL 虽然启动了，但是无法正常使用，无法写入数据库，只能读取。这时候需要备份数据库。

### 2. 备份数据库
使用你习惯的软件或命令备份数据库，一定要检查备份的数据库是否完整。  
~~除非你想体验删库跑路的感觉~~

### 3. 删除数据库文件，重建数据库
注释或者删除第二步中在 MySQL 配置文件中添加的内容，然后删除 MySQL 数据库文件。
进入到 MySQL 的数据文件夹，直接删除数据库名称的文件夹，比如 `test` 数据库的文件夹就是 `test`。

```bash
cd /var/lib/mysql
rm -rf test
```

删除业务数据库后，重启 MySQL，还原数据库备份。

至此，数据库已经恢复正常。祝你好运。

## 参考资料
> [利用 Forcing InnoDB Recovery 特性解决 MySQL 重启失败的问题 - GlonHo - 博客园](https://www.cnblogs.com/glon/p/6728380.html)  
> [MySQL :: MySQL 5.7 Reference Manual :: 15.21.2 Forcing InnoDB Recovery](https://dev.mysql.com/doc/refman/5.7/en/forcing-innodb-recovery.html)  
