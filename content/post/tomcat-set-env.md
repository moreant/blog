---
title: "Tomcat 设置环境变量"
slug: "tomcat-set-env"
date: 2022-04-25T10:17:22+08:00
description: 妈妈再也不用担心我每次都要改配置文件了
tags: 
    - java
categories:
    - dev
---

在 tomcat 的 bin 目录下新建 setenv 文件， Linux 系统用 sh, Windows 系统用 bat

setenv.sh

```ini
JAVA_OPTS="$JAVA_OPTS -Dspring.profiles.active=dev -Dfile.encoding=UTF-8"
```

setenv.bat
```ini
set "JAVA_OPTS=%JAVA_OPTS% -Dfile.encoding=UTF-8 -Dlog4j2.formatMsgNoLookups=true -Dspring.profiles.active=dev"
```
