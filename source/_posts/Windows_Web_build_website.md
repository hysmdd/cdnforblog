---
title: Windows  Web服务器创建网站(2)
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 服务器
date: 2020-02-14 22:22:22
comments: true
tags:  
	- 软考
	- IIS
	- Web服务器
---
创建一个新的网站，并将一些知识点标记了出来，学会创建一个新的网站，并且知道参数的作用是本次的目的。
<!-- more -->
##								IIS新增一个网站

1.	双击<kbd>网站</kbd>，点击右侧<kbd>添加网站</kbd>。

![](https://zhengyuanyuan520.cn/images/softexam/AddWeb/photo1.png)

2.	此时会出现<kbd>添加网站</kbd>的对话框。<kbd>网站名称</kbd>和<kbd>物理路径</kbd>按需求填写和选择即可。

![](https://zhengyuanyuan520.cn/images/softexam/AddWeb/photo2.png) 

3.	此时我们来到<kbd>绑定</kbd>栏，找到<kbd>类型</kbd>复选框。

![](https://zhengyuanyuan520.cn/images/softexam/AddWeb/photo3.png)

>HTTP：默认端口80，以明文的方式进行传输，对于一般博客类网站可能会没有什么很大的问题，但是不适用于对安全性要求较高的场合，例如涉及金融，网购的一些涉及个人隐私的网站就不适用于HTTP了，现在很多网站都会使用HTTPS协议进行传输以确保数据安全。如果发现有使用HTTP方式进行传输的网站，千万不要输入银行卡等重要隐私数据以防泄露。

>HTTPS: 默认端口443，以加密的方式进行传输，使用HTTPS协议需要申请CA证书，常见的有SSL证书。通过HTTPS传输的网站最大的特点便是安全，为用户的隐私提供了保障。

4.	找到<kbd>IP地址</kbd>复选框。

![](https://zhengyuanyuan520.cn/images/softexam/AddWeb/photo4.png)
>全部未分配：如果电脑有多张网卡，则可以通过多张网卡的任何一个IP地址进行新增网站的访问。
>
>如果选择了其中任何一个IP，则表示只能通过选择的IP访问新增的网站。


5.	<kbd>主机名</kbd>，此时不用填写：

>这里我们配置与否都没有任何作用，因为目前还没有搭建DNS服务器，所有域名无法解析，暂时不用填。

6.	填写完成后点击<kbd>确定</kbd>。

![](https://zhengyuanyuan520.cn/images/softexam/AddWeb/photo5.png)

7.	左侧如果有你刚刚新建的网站名，表明新建成功。

![](https://zhengyuanyuan520.cn/images/softexam/AddWeb/photo6.png)