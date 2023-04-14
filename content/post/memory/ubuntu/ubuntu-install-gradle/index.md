---
title: 'Ubuntu 安装 Gradle'
date: 2023-03-03T00:02:22+08:00
slug: 'ubuntu-install-gradle'
image: ubuntu-install-gradle.webp
categories:
  - memory
tag:
  - Linux
  - Ubuntu
---

```
INSTALL_GRADLE_VERSION=5.6.4
```

```bash
wget -P /tmp  https://downloads.gradle-dn.com/distributions/gradle-$INSTALL_GRADLE_VERSION-bin.zip
```

```bash
sudo mkdir -p /opt/gradle
```

```bash
sudo unzip /tmp/gradle-$INSTALL_GRADLE_VERSION-bin.zip -d /opt/gradle
```

```bash
sudo ln -s /opt/gradle/gradle-${INSTALL_GRADLE_VERSION} /opt/gradle/latest
```

```bash
sudo vim /etc/profile.d/gradle.sh
```

```bash
# /etc/profile.d/gradle.sh
export GRADLE_HOME=/opt/gradle/latest
export PATH=${GRADLE_HOME}/bin:${PATH}
```

```bash
sudo chmod +x /etc/profile.d/gradle.sh
```

```bash
source /etc/profile.d/gradle.sh
```

```bash
gradle -v
```

> 参考地址  
> https://linuxize.com/post/how-to-install-gradle-on-ubuntu-20-04/

