---
title: GRE VPN练习
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 网络安全
date: 2020-03-21 11:30:11
comments: true
tags:  
	- 网络安全
	- 交换机
	- 思科GRE
---



GRE  VPN配置练习

软件：Cisco  Packet  Tracer

<!-- more -->

## 题目要求

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200321110549.png)

```
1、基础配置如下：
    按图中所示配置总公司和分公司中各计算机、服务器、路由器对应端口的IP地址相关信息；
2、在总公司与分公司之间配置GRE隧道技术，实现两地私有地址的内部网络之间可以实现相互通信。 
	（1）在Router0和Router1上配置一条默认路由，实现Internet间互通总公司和分公司
        测试Router0和Router1的公网地址间的互通性
	（2）在Router0和Router1上配置  GRE VPN （tunnel号为1，地址分别为10.1.1.1/30和10.1.1.2/30） 
	（3）在Router0和Router1上配置动态路由rip协议，实现总公司和分公司私网路由
3、测试PC0能否ping通PC5，为什么？
4、分析GRE数据包，了解GRE数据封装格式 
```

## Router 0配置IP地址

```
R0> enable
R0# config terminal
R0(config)# interface fastEthernet 0/0
R0(config-if)# ip address 192.168.75.254 255.255.255.0
R0(config-if)# no shutdown
R0(config-if)# exit
R0(config)# interface serial 0/3/0
R0(config-if)# ip address 58.1.1.1 255.255.255.252
R0(config-if)# exit
```

## Router 1配置IP地址

```
R1> enable
R1# config terminal
R1(config)# interface serial 0/3/0
R1(config-if)# ip address 210.28.144.2 255.255.255.252
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config-if)# interface fastEthernet 0/0
R1(config-if)# ip address 192.168.210.254 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# exit
```

## Router 2配置IP地址

```
R2> enable 
R2# config terminal
R2(config)# interface serial 0/1/0
R2(config-if)# ip address 58.1.1.2 255.255.255.252
R2(config-if)# exit
R2(config)# interface  fastEthernet 0/0
R2(config-if)# ip address 63.1.1.1 255.255.255.0
R2(config-if)# exit
R2(config)# interface serial 0/0/0
R2(config-if)# ip address 210.28.144.1 255.255.255.252
R2(config-if)# no shutdown 
```

## Router 0配置静态路由

```
R0(config)# ip route 0.0.0.0 0.0.0.0 58.1.1.2
```

## Router 1配置静态路由

```
R1(config)# ip route 0.0.0.0 0.0.0.0 210.28.144.1
```

## 测试Router 0和Router 1的公网地址互通性

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200321111609.png)

## Router 0配置GRE VPN

```
R0(config)# interface tunnel 1
R0(config-if)# ip address 10.1.1.1 255.255.255.252
R0(config-if)# tunnel source serial 0/3/0
R0(config-if)# tunnel destination 210.28.144.2 
R0(config-if)# exit
```

## Router 1配置GRE VPN

```
R1(config)# interface tunnel 1
R1(config-if)# ip address 10.1.1.2 255.255.255.252
R1(config-if)# tunnel source serial 0/3/0
R1(config-if)# tunnel destination 58.1.1.1 
R1(config-if)# exit
```

## Router 0配置rip

```
R0(config)# router rip 
R0(config-router)# version 2
R0(config-router)# no auto-summary 
R0(config-router)# network 192.168.75.0 
R0(config-router)# network 10.1.1.1
```

## Router 1配置rip

```
R1(config)# router rip 
R1(config-router)# version 2
R1(config-router)# network 192.168.210.0
R1(config-router)# network 10.1.1.2
```

## 测试PC0能否ping通PC5，为什么？

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200321112346.png)

```
解析：PC0可以ping通PC5。因为我们已经配置了隧道，且配置了rip路由，内网地址会通过隧道进行传输，而不会直接从公网进行传输。
```

## 分析GRE数据包，了解GRE数据封装格式

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200321112805.png)

```
解析：当tunnel口收到来自网络层的数据包后，网络层的GRE模块会在原IP包之前加上GRE头部，然后在GRE头部前加上新的IP头部。最后，路由器根据新IP头部进行路由。
```

