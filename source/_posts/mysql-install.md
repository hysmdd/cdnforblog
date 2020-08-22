---
title: MySQL压缩包版安装方法
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 数据库
date: 2020-06-13 12:00:00
music:
  type: song  
  id: 1425626819
comments: true
---

MySQL虽然提供了msi的安装包方式，但是最新版的会默认安装在C盘，而压缩版的我们只需要将文件夹放在自己想放的位置，配置即可使用。接下来我们介绍一下MySQL压缩包安装方式。

<!-- more -->

## 下载压缩包

首先我们到MySQL官网下载[MySQL的压缩包](https://dev.mysql.com/downloads/mysql/)，MySQL提供了压缩包和安装包两种方式，两种方式的区别是压缩包解压之后配置一下就可以使用，而<kbd>.msi</kbd>的安装包安装较为繁琐，故我们介绍压缩包的方式。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613101840.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613102214.png)

## 解压压缩包

解压之后我们会得到下图所示的文件及文件夹

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613102143.png)

## MySQL安装

### 以管理员身份运行<kbd>cmd</kbd>

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613102404.png)

### 进入到解压根目录/bin目录下

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613102633.png)

### 创建配置文件my.ini

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613115839.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613102927.png)

```
# 设置mysql的安装目录  
basedir=D:\\mysql-8.0.20-winx64
# 设置mysql数据库的数据的存放目录  
datadir=D:\\mysql-8.0.20-winx64\\data  
```

{% note success,  **basedir和datadir设置时需要注意的是如果使用“\”请使用双“\\”来分割目录，如果不使用这种可以使用单“/”** %}

### 将my.ini剪切到bin目录下

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613103046.png)

### 新建data文件夹

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613103557.png)

### 初始化MySQL数据目录

执行命令<kbd>mysqld --initialize</kbd>

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613103303.png)

运行完之后就会发现在我们新建的data文件夹生成了很多文件

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613103432.png)

### 报错

如果出现了下面的提示，说明没有安装VC++2015运行库，MySQL运行需要这个运行库，可以去微软官网下载。没有出现报错则跳过该步骤。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613103812.png)

进入微软官网搜索并下载

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613103926.png)

### 获取初始化数据库随机密码

执行完上一步之后，在data目录下生的文件有一个.err文件，这里面有初始化的密码。我们编辑打开此文件，找到密码。该文件命名规则是【电脑用户名.err】如下图

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613104100.png)

找到我们的随机密码

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613104246.png)

### 安装MySQL服务

执行命令<kbd>mysqld --install mysql</kbd>

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613104649.png)

### 启动MySQL服务

执行命令<kbd>net  start  mysql </kbd>

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613113631.png)

### 配置环境变量

<kbd>此电脑</kbd>右键---><kbd>属性</kbd>---><kbd>高级系统设置</kbd>---><kbd>环境变量</kbd>

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613114009.png)

找到<kbd>PATH</kbd>变量，推荐配置在用户变量。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613114042.png)

将MySQL文件夹的bin目录的路径复制，点击右侧新建，添加到环境变。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613114137.png)

{% note success, 配置完成后记得点击确定，有两个地方需要点击确定。 %}

## MySQL连接

### 登录连接MySQL

输入<kbd>mysql  -u  root  -p</kbd>，输入我们刚刚获取到的随机密码。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613114457.png)

出现下面的提示又电脑的路径变成了<kbd>mysql> </kbd>表示我们连接数据库成功。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200613114553.png)

### 修改密码

输入<kbd>ALTER USER 'root'@'localhost' IDENTIFIED BY '密码';</kbd>

{% note success,  修改密码成功会提示<kbd>Query OK, 0 rows affected(0.04sec);</kbd> %}

### 退出重新登录

```mysql
exit
mysql -u root -p
```

