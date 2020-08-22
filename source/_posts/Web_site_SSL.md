---
title: Web站点数字证书(5)
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 服务器
date: 2020-02-15 19:29:30
music:
  type: song  
  id: 1357825630
comments: true
tags:  
	- 软考
	- IIS
	- Web服务器
---
内容： Web站点数字证书
难度： ★★★★☆
<!-- more -->



> Web站点数字证书的申请和安装包括3个部分：申请数字证书、下载数字证书、安装数字证书。

## 申请数字证书

### 1.添加CA证书服务。

> 【开始】--->【管理工具】--->【服务器管理器】--->【角色】--->【添加角色】--->勾选【Active Directory证书服务】。

> 开始--> 管理工具 --> 服务器管理器 

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image001.png)
> 角色 --> 添加角色

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image003.png)
> 下一步

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image005.png)
> 勾选【Active Directory证书服务】，点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image007.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image009.png)
> 勾选【证书颁发机构】和【证书颁发机构Web注册】，点击下一步。

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image011.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image013.png)
> 选择【根CA】，点击下一步。

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image015.png)
> 选择【新建秘钥】，点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image017.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image019.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image021.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image023.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image025.png)
> 检查无误，点击【安装】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image027.png)
> 等待安装完成

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image029.png)
> 点击【关闭】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image031.png)

### 2.创建证书申请

> 选择【角色】-->【Web服务器(IIS)】-->【Internet信息服务】-->右侧主机-->【服务器证书】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image033.png)
> 选择到期日期为5年之后的，点击右侧【创建证书申请】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image035.png)
> 通用名称须填写网站绑定的IP，其他可随意填写，填写完成点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image037.png)
> 点击【下一步】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image039.png)
> 选择路径并设置文件名，点击【完成】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image041.png)
> 完成后会回到此界面

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image043.png)

## 下载数字证书
### 1.申请证书

> 浏览器地址栏输入localhost/certsrv

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image045.png)
> 点击【申请证书】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image047.png)
> 点击【高级证书申请】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image049.png)
> 找到之前下载的文件，打开并复制所有内容

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image051.png)
> 在【保存的申请】文本框将复制的内容粘贴，点击【提交】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image053.png)
> 提示证书正在挂起，以及ID

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image055.png)
### 2.颁发证书

> 【角色】-->【Active  Directory 证书服务】-->【Win ...】-->【挂起的申请】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image057.png)
> 找到刚刚对应的ID，右键，【所有任务】--->【颁发】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image059.png)
> 点击左侧【颁发的证书】，查看对应的ID证书是否已颁发

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image061.png)
### 3.下载证书

> 浏览器地址栏输入localhost/certsrv，点击【查看挂起的证书申请的状态】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image063.png)
> 点击【保存的申请证书】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image065.png)
> 点击【下载证书】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image067.png)
## 安装数字证书
### 1.安装数字证书

> 找到刚刚下载证书的文件

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image069.png)
> 选择【Web服务器(IIS)】-->【Internet信息服务(IIS)】-->【Win...】-->【服务器证书】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image071.png)
> 选择到期时间为5年后的，点击【完成证书申请】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image073.png)
> 选择刚刚浏览器下载的证书文件，输入名称，点击【确定】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image075.png)
>  在服务器证书列表查看新证书是否出现在列表

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image077.png)

### 2.绑定网站类型为HTTPS

> 选择自己的网站，点击右侧【绑定】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image079.png)
> 点击【添加】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image081.png)
>类型为HTTPS，IP为网站绑定IP，选择SSL证书，点击【确定】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image083.png)

### 3.启用SSL

> 选择【SSL设置】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image084.png)
> 勾选【要求SSL】，将客服证书设置为【接受】，点击【应用】

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image086.png)

## 最终效果
> 接下来就可以用https访问网站啦

![](https://zhengyuanyuan520.cn/images/softexam/SSL/image088.png)