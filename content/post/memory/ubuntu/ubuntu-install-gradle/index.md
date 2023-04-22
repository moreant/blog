---
title: 'Ubuntu 安装 Gradle'
date: 2023-03-03T00:02:22+08:00
slug: 'ubuntu-install-gradle'
image: ubuntu-install-gradle.webp
categories:
  - memory
tags:
  - Linux
  - Ubuntu
  - Gradle
  - Java
---

指定期望安装的版本  
```
INSTALL_GRADLE_VERSION=5.6.4
```

下载 gradle。如果速度慢，可以参考[这里](/p/gradle-china-cdn/) 替换源
```bash
wget -P /tmp  https://downloads.gradle-dn.com/distributions/gradle-$INSTALL_GRADLE_VERSION-bin.zip
```

创建 Gradle 安装目录   
```bash
sudo mkdir -p /opt/gradle
```

解压到安装目录
```bash
sudo unzip /tmp/gradle-$INSTALL_GRADLE_VERSION-bin.zip -d /opt/gradle
```

将来可能会安装多个版本，使用用软连接指向某个版本
```bash
sudo ln -s /opt/gradle/gradle-${INSTALL_GRADLE_VERSION} /opt/gradle/latest
```

在 profile.d 中添加 Gradle 的环境变量，这样在系统启动时就会自动加载添加 Gradle 的环境变量脚本了
```bash
sudo vim /etc/profile.d/gradle.sh
```

`gradle.sh` 内容如下
```bash
# /etc/profile.d/gradle.sh
export GRADLE_HOME=/opt/gradle/latest
export PATH=${GRADLE_HOME}/bin:${PATH}
```

将 `gradle.sh` 文件设置为可执行
```bash
sudo chmod +x /etc/profile.d/gradle.sh
```

使配置立即生效
```bash
source /etc/profile.d/gradle.sh
```

检查是否安装成功
```bash
gradle -v
```

> 参考地址  
> https://linuxize.com/post/how-to-install-gradle-on-ubuntu-20-04/

