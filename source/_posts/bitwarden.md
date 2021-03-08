---
title: centOS 7搭建Bitwarden密码服务器
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Linux
date: 2020-03-31 13:04:14
comments: true
---

您可以在Windows，macOS和Linux发行版上使用Docker容器部署Bitwarden。使用提供的PowerShell和Bash脚本快速入门。在[Docker Hub](https://hub.docker.com/u/bitwarden/)上找到所有Bitwarden映像。

<!-- more -->

## 安装Docker

1. 安装所需的软件包。`yum-utils`提供了`yum-config-manager` 效用，并`device-mapper-persistent-data`和`lvm2`由需要 `devicemapper`存储驱动程序。

```
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```

2.使用以下命令来设置**稳定的**存储库。

```
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

3.安装*最新版本*的Docker Engine-Community和containerd，或者转到下一步安装特定版本：

```
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

如果提示您接受GPG密钥，请验证指纹是否匹配 `060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35`，如果是，则接受它。

4.启动Docker。

```
$ sudo systemctl start docker
```

5.设置开机自启动。

```
$ sudo systemctl enable docker
```

## 安装Docker Compose

1.运行以下命令以下载Docker Compose的当前稳定版本：

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

2.将可执行权限应用于二进制文件：

```
sudo chmod +x /usr/local/bin/docker-compose
```

**注意**：如果命令`docker-compose`在安装后失败，请检查路径。您也可以创建指向`/usr/bin`或路径中任何其他目录的符号链接。

例如：

```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

3.测试安装：

```
$ docker-compose --version
docker-compose version 1.25.4, build 1110ad01
```

## 安装Bitwarden

```
curl -s -o bitwarden.sh \
    https://raw.githubusercontent.com/bitwarden/server/master/scripts/bitwarden.sh \
    && chmod +x bitwarden.sh
./bitwarden.sh install
./bitwarden.sh start
```