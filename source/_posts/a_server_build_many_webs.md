---
title: 一台服务器创建多个Web站点(4)
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 服务器
date: 2020-02-15 16:45:30
music:
  type: song  
  id: 1382596189
comments: true
tags:  
	- 软考
	- IIS
	- Web服务器
---
内容： 一台服务器创建多个Web站点
难度： ★★★☆☆
<!-- more -->



> 实现虚拟主机一般有3种方式：
> * 使用不同的IP
> * 使用相同的IP，不同的TCP端口
> * 使用相同的IP和TCP端口，不同的主机头（域名）

---
## 			使用不同的IP
### 1.新建一个网站
> 现在实验的是使用不同的IP，所以新建网站绑定的IP地址要选择与之前新建网站的IP地址不能相同

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p1.png)

### 2. 将网页文件放进网站根目录

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p2.png)

### 3.网站不同IP访问
> 现在我们就可以通过不同的IP地址进行访问
> qh：192.168.74.128:80
> qh2 : 192.168.74.129:80

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p3.png)
![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p4.png)

## 		使用相同的IP，不同的TCP端口
### 1.新建一个网站
> 现在实验的是使用相同的IP，但是使用不同的TCP端口，所以我们选择与之前的网站IP地址相同。

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p5.png)

### 2.将网页文件放进网站根目录

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p6.png)

### 3.通过相同IP不同端口访问
> 现在我们就可以通过相同的IP，不同的端口进行访问
> qh：192.168.74.128:80
> qh3:192.168.74.128:8080

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p7.png)
![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p8.png)


## 使用相同的IP和TCP端口，不同的主机名（域名）
### 1.新建一个网站

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p9.png)

### 2.将另一个网站绑定域名

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p10.png)

### 3.更改host实现本地域名解析
> 由于我们现在并没有使用DNS来进行域名解析，我们本地实验所有这里就以更改host文件来实现本地域名解析

### 4.找到记事本，以管理员身份运行。

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p11.png)

### 5.点击【文件】--->【打开】

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p12.png)

### 6.选择host文件并打开
> 路径：【C:\Windows\System32\drivers\etc】，找到host文件，如果没有则在右下角选择展示所有文件。

### 7.添加域名解析
> 在host文件最下面加上：
> 192.168.74.128        www.qinhao.com
> 192.168.74.128        tsg.qinhao.com

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p13.png)

### 8.浏览器访问www.qinhao.com

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p14.png)

### 9.浏览器访问tsg.qinhao.com

![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p15.png)
![](https://zhengyuanyuan520.cn/images/softexam/twoWeb/p16.png)


### 10.注意事项
> 本方法只能使用域名对网站进行访问，不可以通过IP对网站进行访问。