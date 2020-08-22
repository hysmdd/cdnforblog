---
title: 非华为电脑使用多屏协同
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 软件破解
date: 2020-05-19 11:42:14
music:
  type: song  
  id: 1425626819
comments: true
---



绕过华为对非华为电脑管家的限制，一键安装PCManager（不需要改BOIS）

PCManager管理功能，启动、关闭、服务控制等。

提供极客模式。

<!-- more -->

## 前期准备

{% checkbox green checked, 具有多屏协同功能的华为或荣耀手机 %}

 {% checkbox green checked, 一台带蓝牙和无线网卡的win 10电脑 %}

## 安装华为的电脑管家

华为电脑管家的安装包大家可以关注我的微信公众号，回复“多屏协同”即可获取安装包及安装工具下载地址。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/weixin.jpg)

### 解压文件

解压之后会得到下图的文件。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200518202819.png)

### 启动安装工具

1. 将之前安装的电脑管家完全卸载，删除<kbd>C:\Program Files\Huawei\PCManager</kbd>目录所有文件。
2. 重启电脑。
3. <kbd>PCManagerMgr.exe</kbd>右键，以<kbd>管理员身份运行</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519100611.png)

### 卸载之前的版本

{% note success, 如果之前安装过旧版本请执行此步骤，没有安装过请跳过 %}

点击<kbd>卸载</kbd>，会弹出华为电脑管家的卸载界面，点击<kbd>我要卸载</kbd>，等待卸载完成，出现<kbd>电脑管家已卸载</kbd>，点击<kbd>完成</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519101314.png)

### 重启电脑

{% note success, 卸载完成后需要重启电脑，然后再次打开工具。 %}

### 获取口令

关注<kbd>汉客儿</kbd>的微信公众号，回复关键字<kbd>口令</kbd>，将获取到的口令复制到下图方框位置。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519101920.png)

### 开始安装

复制口令后，点击<kbd>安装</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519102200.png)

点击<kbd>安装</kbd>后会出现<kbd>正在安装hw电脑管家...</kbd>，等待弹出华为电脑管家的安装界面。<red>注意：系统必须是win10的，我这里由于安装过了，用虚拟机展示的界面。</red>

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519102314.png)

点击<kbd>立即安装</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519102434.png)

安装完成后会到工具，看到<kbd>当前管家已经xx，尽情享受吧</kbd>，此时软件已经安装完成。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519102713.png)

### 检查服务是否运行

检查上图中右边的服务是否是<kbd>运行中</kbd>的状态，如果是<kbd>未运行</kbd>则点击后面的<kbd>运行</kbd>按钮。

## 连接手机

点击左侧<kbd>我的手机</kbd>，然后点击<kbd>立即连接</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519110854.png)

选择<kbd>扫码连接</kbd>，手机打开<kbd>华为浏览器</kbd>，扫码后点击<kbd>连接</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519111026.png)

点击<kbd>连接</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/5382a561154e1d7697f13ce372a3516.jpg)

点击<kbd>允许</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519111423.png)

连接成功之后会出现手机的型号以及存储空间信息。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519113119.png)

## 多屏协同

点击<kbd>多屏协同</kbd>。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519113243.png)

此时就可以使用<kbd>多屏协同</kbd>功能啦。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519113426.png)

{% note success, 建议电脑和手机处于5GHz频带的wifi可提升流畅度。 %}

