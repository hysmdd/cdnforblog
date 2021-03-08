---
title: IPSec VPN配置练习
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 网络安全
date: 2020-03-25 12:30:11
comments: true
tags:  
	- 网络安全
	- 交换机
	- 思科
---

IPSec VPN配置 

软件：Cisco Packet  Tracer

<!-- more -->

## 题目要求

实验网络拓扑图如图所示

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325101139.png)

1、基础配置如下：
    (1)按图中所示配置总公司和分公司中各计算机、服务器、路由器对应端口的IP地址相关信息；
    (2)在Router0和Router1上配置一条默认路由，实现Internet间互通
    (3) 测试Router0和Router1的公网地址间的互通性
2、在总公司与分公司之间配置IPsec VPN，实现两地私有地址的内部网络之间可以实现相互通信。 
（1） 配置 IKE（ISAKMP）策略： 
策略序号为1，加密算法为aes，Hash 算法为MD5，密钥算法（Diffie-Hellman）为group 2，认证方式（Authentication）为pre-share。 
（2）定义认证标识：预共享密码为tx18 
（3）配置 IPsec transform： 
定义transform set命名为tx18set，加密算法为esp-3des， HMAC 算法为esp-MD5-HMAC 
（4）定义感兴趣流量： 
用扩展acl 180来定义通过 VPN 传输的流量 
（5）创建 crypto map： 
定义transform set命名为tx18map，将之前定义的 ACL，加密数据发往的对端，以及 IPsec transform 结合在 crypto map中 
（6）将 crypto map 应用于对应接口 
3、测试PC0能否ping通PC5，为什么？
4、分析IPSec VPN数据包，了解IPSec VPN数据封装格式 
5、选做：
在公司边界路由器上做NAT（数据自选），实现总公司和分公司的PC可以ping通公网PC

## 配置Router  0端口地址

```
R0> enable												#进入特权模式
R0# config terminal										#进入全局模式
R0(config)# interface FastEthernet 0/0					#进入Fa0/0端口
R0(config-if)# ip address 192.168.123.254 255.255.255.0	#配置IP地址和子网掩码
R0(config-if)# no shutdown								#启用端口
R0(config-if)# exit										#退出Fa0/0端口
R0(config)# interface Serial 0/3/0						#进入Se0/3/0端口
R0(config-if)# ip address 58.1.1.1 255.255.255.252		#配置IP地址和子网掩码
R0(config-if)# no shutdown								#启用端口
R0(config-if)# exit										#退出Se0/3/0端口
```

## 配置Router  1端口地址

```
R1> enable												#进入特权模式
R1# config terminal										#进入全局模式
R1(config)# interface FastEthernet 0/0					#进入Fa0/0端口
R1(config-if)# ip address 192.168.100.254 255.255.255.0	#配置IP地址和子网掩码
R1(config-if)# no shutdown								#启用端口
R1(config-if)# exit										#退出Fa0/0端口
R1(config)# interface Serial 0/3/0						#进入Se0/3/0端口
R1(config-if)# ip address 210.28.144.2 255.255.255.252	#配置IP地址和子网掩码
R1(config-if)# no shutdown								#启用端口
R1(config-if)# exit										#退出Se0/3/0端口
```

## 配置Router  2端口地址

```
R2> enable												#进入特权模式
R2# config terminal										#进入全局模式
R2(config)# interface FastEthernet 0/0					#进入Fa0/0端口
R2(config-if)# ip address 63.1.1.1 255.255.255.0		#配置IP地址和子网掩码
R2(config-if)# no shutdown								#启用端口
R2(config-if)# exit										#退出Fa0/0端口
R2(config)# interface Serial 0/1/0						#进入Se0/1/0端口
R2(config-if)# ip address 58.1.1.2 255.255.255.252		#配置IP地址和子网掩码
R2(config-if)# exit										#退出Se0/1/0端口
R2(config)# interface Serial 0/0/0						#进入Se0/0/0端口
R2(config-if)# ip address 210.28.144.1 255.255.255.252	#配置IP地址和子网掩码
R2(config-if)# no shutdown								#启用端口
R2(config-if)# exit										#退出Se0/0/0端口
```

## Router  0配置静态路由

```
R0(config)# ip route 0.0.0.0 0.0.0.0 58.1.1.2			#配置静态路由
```

## Router  1配置静态路由

```
R0(config)# ip route 0.0.0.0 0.0.0.0 210.28.144.1		#配置静态路由
```

## Router  0和Router  1公网间互通性

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325110016.png)

```
Router 0和Router 1公网地址间可以互通。
```

## Router  0配置IPsec  VPN

（1） 配置 IKE（ISAKMP）策略

策略序号为1，加密算法为aes，Hash 算法为MD5，密钥算法（Diffie-Hellman）为group 2，认证方式（Authentication）为pre-share。 

```
R0(config)# crypto isakmp policy 1				#建立IKE策略，优先级为1
R0(config-isakmp)# encryption aes 				#使用AES加密方式	
R0(config-isakmp)# hash md5						#指定Hash算法为MD5
R0(config-isakmp)# authentication pre-share		#使用预共享的密码进行身份验证
R0(config-isakmp)# group 2						#指定秘钥位数，group2安全性更高
```

（2）定义认证标识：预共享密码为tx18 

```
R0(config)# crypto isakmp key tx18 address 210.28.144.2		
#设置要使用的预共享秘钥和指定VPN对端路由器的IP地址。
```

（3）配置 IPsec transform： 
定义transform set命名为tx18set，加密算法为esp-3des， HMAC 算法为esp-MD5-HMAC 

```
R0(config)# crypto ipsec transform-set tx18set esp-3des esp-md5-hmac		
#配置IPSec交换集，名称为tx18set，两端的名字可以不一样，但其它参数必须一致。
```

（4）定义感兴趣流量： 
用扩展acl 180来定义通过 VPN 传输的流量

```
R0(config)# access-list 180 permit ip 192.168.123.0 0.0.0.255 192.168.100.0 0.0.0.255	#定义感兴趣数据，IPSec  VPN地址为双方内网地址。
```

（5）创建 crypto map： 
定义transform set命名为tx18map，将之前定义的 ACL，加密数据发往的对端，以及 IPsec transform 结合在 crypto map中 

```
R0(config)# crypto map tx18map 1 ipsec-isakmp 		#创建加密图	
R0(config-crypto-map)# set peer 210.28.144.2		#标识对方路由器IP地址
R0(config-crypto-map)# set transform-set tx18set 	#指定加密图使用的IPSec交换集
R0(config-crypto-map)# match address 180			#用ACL定义加密的通信
```

（6）将 crypto map 应用于对应接口

```
R0(config)# interface Serial 0/3/0		#进入Se0/3/0端口
R0(config-if)# crypto map tx18map		#应用加密图到接口
```

## Router  1配置IPsec  VPN

（1） 配置 IKE（ISAKMP）策略

策略序号为1，加密算法为aes，Hash 算法为MD5，密钥算法（Diffie-Hellman）为group 2，认证方式（Authentication）为pre-share。 

```
R0(config)# crypto isakmp policy 1					#建立IKE策略，优先级为1
R0(config-isakmp)# encryption aes 					#使用AES加密方式	
R0(config-isakmp)# hash md5							#指定Hash算法为MD5
R0(config-isakmp)# authentication pre-share			#使用预共享的密码进行身份验证
R0(config-isakmp)# group 2							#指定秘钥位数，group2安全性更高
```

（2）定义认证标识：预共享密码为tx18 

```
R0(config)# crypto isakmp key tx18 address 58.1.1.1		#定义预共享密码
```

（3）配置 IPsec transform： 
定义transform set命名为tx18set，加密算法为esp-3des， HMAC 算法为esp-MD5-HMAC 

```
R0(config)# crypto ipsec transform-set tx18set esp-3des esp-md5-hmac		#配置IPSec交换集，名称为tx18set，两端的名字可以不一样，但其它参数必须一致。
```

（4）定义感兴趣流量： 
用扩展acl 180来定义通过 VPN 传输的流量

```
R0(config)# access-list 180 permit ip 192.168.100.0 0.0.0.255 192.168.123.0 0.0.0.255	#定义感兴趣数据，IPSec  VPN地址为双方内网地址。
```

（5）创建 crypto map： 
定义transform set命名为tx18map，将之前定义的 ACL，加密数据发往的对端，以及 IPsec transform 结合在 crypto map中 

```
R0(config)# crypto map tx18map 1 ipsec-isakmp 		#创建加密图
R0(config-crypto-map)# set peer 58.1.1.1			#标识对方路由器IP地址	
R0(config-crypto-map)# set transform-set tx18set 	#指定加密图使用的IPSec交换集
R0(config-crypto-map)# match address 180			#用ACL定义加密的通信
```

（6）将 crypto map 应用于对应接口

```
R0(config)# interface Serial 0/3/0			#进入Se0/3/0端口
R0(config-if)# crypto map tx18map			#应用加密图到接口
```

## 测试PC0能否ping通PC5，为什么？

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325113219.png)

```
解析：PC 0可以ping通PC 5，因为此时我们配置了IPSec VPN，分公司之间的访问会通过IPSec VPN隧道进行访问。
```

## 分析IPSec VPN数据包，了解IPSec VPN数据封装格式

进入仿真模式，用PC0  ping  PC5，并单步运行，直到面板上出现Last  Device为Switch  0，At  Device为Router  0的数据包为止，查看该数据包的Inbound  PDU  Details和 OurBound  PDU  Details。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325124408.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325124215.png)

```
观察第一张图可知：封装前的数据包源IP地址为192.168.123.10，目的IP地址为192.168.100.20。观察第二张图可知：封装后在原始IP头之前增加了新的IP头和ESP头，在新的IP头中源IP地址为58.1.1.1，目的地址为210.28.144.2，IPSec封装已经完成。ESP头中的信息如下：ESP SPI为1469921110，ESP序号为0，ESP的加密方式为3DES，ESP认证方式为MD5。
```

## Router  0边界配置NAT

```
R0(config)# interface FastEthernet 0/0
R0(config-if)# ip nat inside
R0(config-if)# exit
R0(config)# interface Serial 0/3/0
R0(config-if)# ip nat outside
R0(config-if)# exit
R0(config)# ip nat pool natpool 100.1.1.1 100.1.1.2 netmask 255.255.255.252
R0(config)# ip nat inside source list 101 pool natpool overload
```

## Router  1边界配置NAT

```
R1(config)# interface FastEthernet 0/0
R1(config-if)# ip nat inside
R1(config-if)# exit
R1(config)# interface Serial 0/3/0
R1(config-if)# ip nat outside
R1(config-if)# exit
R1(config)# ip nat pool natpool 200.1.1.1 200.1.1.3 netmask 255.255.255.248
R1(config)# ip nat inside source list 101 pool natpool overload
```

## 出现新问题

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325113551.png)

```
配置了NAT之后我们发现：PC0 不能ping通PC 5了。这是因为IPSec与NAT发生了冲突，路由器对数据包的处理流程是先进行NAT转换，然后进行IPSec封装。所以要对进行IPSec封装的数据流进行一些相关设置，使该数据流不被NAT转换，这样才能成功进行IPSec通信。
```

## 解决问题

### Router  0添加配置

```
R0(config)# access-list 101 deny ip 192.168.123.0 0.0.0.255 192.168.100.0 0.0.0.255
R0(config)# access-list 101 permit ip 192.168.123.0 0.0.0.255 any
```

### Router  1添加配置

```
R1(config)# access-list 101 deny ip 192.168.100.0 0.0.0.255 192.168.123.0 0.0.0.255
R1(config)# access-list 101 permit ip 192.168.100.0 0.0.0.255 any
```

## 测试结果

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325113219.png)

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200325115020.png)

```
我们发现总公司和分公司的PC可以ping通公网PC，且解决了上面出现的配置NAT之后内网间无法互相访问的问题。
```

