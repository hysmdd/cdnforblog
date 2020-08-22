---
title: Windows  Web服务器环境搭建(1)
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 服务器
date: 2020-02-14 21:21:21
music:
  type: song  
  id: 36270426
comments: true
tags:  
	- 软考
	- IIS
	- Web服务器
---
IIS是一种Web（网页）服务组件，其中包括Web服务器、FTP服务器、NNTP服务器和SMTP服务器，分别用于网页浏览、文件传输、新闻服务和邮件发送等方面，它使得在网络（包括互联网和局域网）上发布信息成了一件很容易的事。
<!-- more -->

##								Windows  Web服务器配置

1.	我们需要安装IIS工具才能搭建网站。我们依次点击<kbd>开始</kbd> ---> <kbd>管理工具</kbd> ---> <kbd>服务器管理器</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo1.png)
2.	进入<kbd>服务器管理器</kbd>界面后，我们点击<kbd>角色</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo2.png) 
3.	点击<kbd>添加角色</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo3.png)
4.	此时我们会进入<kbd>添加角色向导</kbd>，如果不想每次提醒的话可以勾选下面的<kbd>默认情况下将跳过此页</kbd>，点击<kbd>下一步</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo4.png)
5.	此时我们进入到<kbd>选择服务器角色</kbd>，勾选<kbd>Web服务器(IIS)</kbd>，点击<kbd>下一步</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo5.png)
6.	此时会出现Web服务器的简介和注意事项，我们直接点击<kbd>下一步</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo6.png)
7.	选择需要安装的服务，这里我就直接全部勾选，全部安装了（建议将FTP也勾选上），点击<kbd>下一步</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo7.png)
8.	确认信息，确保无误之后我们就可以点击<kbd>安装</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo8.png)
9.	等待安装。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo9.png)
10.	 安装完成以后，点击<kbd>关闭</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo10.png)
11.	如果在<kbd>角色摘要</kbd>里面看到了Web服务器(IIS)就表明我们安装成功。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo11.png)
12.	 点击<kbd>角色</kbd>前面的“+”号将其展开，找到<kbd>Web服务器(IIS)</kbd>将其展开，点击<kbd>Internet信息服务(IIS)</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo12.png)
13.	将标记处依次展开，站到<kbd>网站</kbd>，展开找到<kbd>Default Web Site</kbd>。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo13.png)
14.	双击<kbd>Default Web Site</kbd>，点击右侧<kbd>浏览 *:80 （http）</kbd>即可查看IIS提供的默认界面。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo14.png)
15.	预览结果。
![](https://www.zhengyuanyuan520.cn/images/softexam/Web/photo15.png)
