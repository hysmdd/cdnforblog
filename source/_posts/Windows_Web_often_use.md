---
title: Windows  Web服务器常用功能(3)
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 服务器
date: 2020-02-15 14:23:30
comments: true
tags:  
	- 软考
	- IIS
	- Web服务器
---
内容： Windows  Web服务器常用功能
难度： ★★★☆☆
<!-- more -->



## 给网站绑定IP地址

1.	双击自己的网站名称，点击右侧【绑定】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p1.png)

2.	点击左边列表中的绑定，点击【编辑】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p2.png)

3.	默认的是HTTP类型，我们不可以进行更改。IP地址分为未分配和单独IP地址，IP地址的内容我们在上一篇文章已经提到了，所以不再叙述。端口号我们可以自行设置。默认是80端口，使用80端口我们就可以直接通过IP地址就可以访问，使用其它端口则需要在IP后面添加端口号，例：192.168.74.128:8080。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p3.png)

4.	选择好IP地址和端口号后，点击【确定】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p4.png)


##	更换自己的网站为默认页
1.	首先我们可以点击右侧【浏览】，进入到网站的主目录。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p5.png)

2.	将自己的网页文件放置到网站主目录。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p6.png)

3.	我们可以打开浏览器输入你自己网站绑定的IP地址，我的是192.168.74.128，端口号是80，那么我们直接在浏览器输入192.168.74.128,当然，输入192.168.74.128:80也会在浏览器自动显示为192.168.74.128。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p7.png)


## 修改默认网页文件
1.	我们可以先查看一下IIS给我们设置的默认访问文件，我们双击自己的网站名，然后找到【IIS】栏里面的【默认文档】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p8.png)

2.	下面列出来的这些就是默认访问文件，也就是我们放在根目录只要是这些文件名都将会设置为首页。如果根目录有多个下面列表的名称的文件，那么会根据列表的顺序进行访问，例如我们根目录同时有Default.htm和index.html，由于Default.htm是在index.html之前的，所以我们打开网页会显示Default.htm的内容。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p9.png)

3.	将index.html设置为优先级最高的文件。点击【index.html】，然后点击右侧【上移】，移到顶部。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p10.png)

4.	假如我们需要设置首页的网页是hello.html，而不是index.html。此时我们可以点击右侧【添加】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p11.png)

5.	此时会弹出【添加默认文档】对话框，输入我们需要设置主页的文件，如:hello.html，点击【确定】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p12.png)

6.	检查添加的网页文件名称是否置顶。可以看到我们新增的网站条目类型为【本地】，一般【本地】的优先级比【继承】高。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p13.png)

7.	刷新浏览器，可以看到我们的已经将主页文件改成了hello.html。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p14.png)

## 	设置网站访问需要验证。

> 验证方式常用的有：
> * Windows身份验证
> * 基本身份验证
> * 匿名身份验证
> * 摘要式身份验证。
---

>
> * 匿名身份验证：允许匿名访问，则不需要验证用户。
> * 基本身份验证：访问网站需要用户输入账户名及密码。但由于采用不加密的Base64编码传输，故传输并不安全。
> * 摘要式身份验证：访问网站也需要用户输入账户名及密码，但采用了MD5的加密方式进行传输，故安全性比基本身份验证高。
> * Windows身份验证：希望客户端使用 NTLM 或 Kerberos 协议进行身份验证，则使用 Windows 身份验证。
---

> 默认开启的是匿名身份验证，如果同时开启了匿名身份验证和其他身份验证，会优先匿名身份认证。
---

> 安全性比较： Windows身份验证 >  摘要式身份验证 >  基本身份验证  >  匿名身份验证

1.	双击【IIS】栏里面的【身份验证】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p15.png)

2.	例如我们要将身份验证方式改为基本身份验证，我们首先需要关闭匿名身份验证。点击【匿名身份验证】，点击右侧【禁用】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p16.png)

3.	然后点击【基本身份验证】，点击右侧【启用】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p17.png)

4.	然后我们去浏览器刷新网页，此时会提醒我们验证身份，输入用户名和密码就可以正常访问，验证失败则会返回401错误。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p18.png)

## 设置IP地址和域限制。
> 设置IP地址和域限制可以限制IP或网段不允许访问网站。

---
1.	双击【IIS】栏的【IP地址和域限制】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p19.png)

2.	拒绝IP或IP网段进行访问，则点击【添加拒绝条目】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p20.png)

3.	可以限制IP地址或者IP地址范围。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p21.png)

4.	也可以拒绝任何人进行访问，直接点击右侧的【编辑功能设置】。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p22.png)

5.	将【未指定的客户端的访问权】设置为拒绝，点击确定，此时任何IP都不可以进行网站的访问了。

![](https://zhengyuanyuan520.cn/images/softexam/idea/p23.png)
