---
title: ACL配置练习
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 网络安全
date: 2020-03-04 12:30:11
comments: true
tags:  
	- 网络安全
	- 交换机
	- 思科
---

为了增强网络的安全性，可以通过防火墙禁止未经授权或可能存在危险的访问进入网络。ACL包过滤技术就是一种被广泛应用于防火墙的网络安全技术。

<!-- more -->

## 任务

### 基础配置任务

```
（1）按图中所示配置各计算机、服务器、路由器对应端口的IP地址相关信息；
（2）在路由器R0、R1、R2上启动rip v2协议，使得全网互通。
```

### ACL配置任务

```
（1）禁止PC0 ping通外网，允许PC2 ping通外网；（标准acl，序号1）
（2）禁止PC2访问服务器Server0的web服务，但可以ping通服务器Server0。（扩展acl，序号101）
```

## 实现步骤

```
1、如图所示，全网由内网1、内网2及ISP（运营商网络：模拟互联网）组成，首先配置各计算机、服务器、路由器对应端口的IP地址相关信息，使用show ip route、ping命令测试网络并记录输出信息。
```

![](https://www.zhengyuanyuan520.cn/images/switch/acl/main_pic.png)

| 设备名称 | 接口    | IP地址            | 网关              |
| -------- | ------- | ----------------- | ----------------- |
| R0       | Fa0/0   | 192.168.22.254/24 |                   |
| R0       | Se0/3/0 | 58.1.1.1/30       |                   |
| R1       | Fa0/0   | 192.168.18.254/24 |                   |
| R1       | Se0/3/0 | 210.28.144.2/30   |                   |
| R2       | Se0/1/0 | 58.1.1.2/30       |                   |
| R2       | Se0/0/0 | 210.28.144.1/30   |                   |
| Server0  |         | 192.168.18.250/24 | 192.168.18.254/24 |
| PC0      |         | 192.168.22.10/24  | 192.168.22.254/24 |
| PC2      |         | 192.168.22.20/24  | 192.168.22.254/24 |
| PC3      |         | 192.168.18.10/24  | 192.168.18.254/24 |
| PC5      |         | 192.168.18.20/24  | 192.168.18.254/24 |

### 基础配置

#### Router0配置Fa0/0端口

```
R0> enable													#进入特权模式
R0# config terminal											#进入全局模式
R0(config)# interface fastEthernet 0/0						#进入Fa0/0端口
R0(config-if)# ip address 192.168.22.254 255.255.255.0		#配置IP和子网掩码
R0(config-if)# no shutdown									#开启端口
R0(config-if)# exit											#退回Fa0/0端口
```

#### Router0配置Se0/3/0端口

```
R0(config)# interface serial 0/3/0							#配置se0/3/0端口
R0(config-if)# ip address 58.1.1.1 255.255.255.252			#配置IP和子网掩码
```

#### Router2配置Se0/1/0端口

```
R2> enable													#进入特权模式
R2# config terminal											#进入全局模式
R2(config)# interface serial 0/1/0							#进入se0/1/0端口
R2(config-if)# ip address 58.1.1.2 255.255.255.252			#配置IP和子网掩码
R2(config-if)# no shutdown 									#开启端口
R2(config-if)# exit											#退出se0/1/0端口
```

#### Router2配置Se0/0/0端口

```
R2(config)# interface serial 0/0/0							#进入se0/0/0端口
R2(config-if)# ip address 210.28.144.1 255.255.255.252		#配置IP和子网掩码
R2(config-if)# no shutdown									#开启端口
R2(config-if)# exit											#退出se0/0/0端口
```

#### Router1配置Se0/3/0端口

```
R1> enable													#进入特权模式
R1# config terminal											#进入全局模式
R1(config)# interface serial 0/3/0							#进入se0/3/0端口
R1(config-if)# ip address 210.28.144.2 255.255.255.252		#配置IP和子网掩码
R1(config-if)# no shutdown									#配置IP和子网掩码
R1(config-if)# exit											#退出se0/3/0端口
```

#### Router1配置Fa0/0端口

```
R1(config)# interface fastEthernet 0/0						#进入Fa0/0端口
R1(config-if)# ip address 192.168.18.254 255.255.255.0		#配置IP和子网掩码
R1(config-if)# no shutdown									#配置IP和子网掩码
```

#### Router0路由表

![](https://www.zhengyuanyuan520.cn/images/switch/acl/router0_table.png)

#### Router1路由表

![](https://www.zhengyuanyuan520.cn/images/switch/acl/router1_table.png)

#### Router2路由表

![](https://www.zhengyuanyuan520.cn/images/switch/acl/router2_table.png)

#### PC0  ping  PC5

![](https://www.zhengyuanyuan520.cn/images/switch/acl/pc0_ping_pc5.png)

### 全网互通（RIP配置)

#### R0:RIP  2配置

```
R0(config)# router rip								#启动rip协议
R0(config-router)# version 2						#指定rip v2版本
R0(config-router)# no auto-summary					#关闭路由器自动汇总功能
R0(config-router)# network 192.168.22.0				#宣告自己的网段
R0(config-router)# network 58.1.1.1					#宣告自己的网段
R0(config-router)# exit								#退出rip配置模式
```

#### R1:RIP  2配置

```
R1(config)# router rip								#启动rip协议
R1(config-router)# version 2						#指定rip v2版本
R1(config-router)# no auto-summary					#关闭路由器自动汇总功能
R1(config-router)# network 192.168.18.0				#宣告自己的网段
R1(config-router)# network 210.28.144.2				#宣告自己的网段
R1(config-router)# exit								#退出rip配置模式
```

#### R2:RIP  2配置

```
R1(config)# router rip								#启动rip协议
R1(config-router)# version 2						#指定rip v2版本
R1(config-router)# no auto-summary					#关闭路由器自动汇总功能
R1(config-router)# network 58.1.1.2					#宣告自己的网段
R1(config-router)# network 210.28.144.1				#宣告自己的网段
R1(config-router)# exit								#退出rip配置模式
```

#### Router0路由表

![](https://www.zhengyuanyuan520.cn/images/switch/acl/Router0_RIP_table.png)

#### Router1路由表

![](https://www.zhengyuanyuan520.cn/images/switch/acl/Router1_RIP_table.png)

#### Router2路由表

![](https://www.zhengyuanyuan520.cn/images/switch/acl/Router2_RIP_table.png)

#### PC0  ping  PC5

![](https://www.zhengyuanyuan520.cn/images/switch/acl/PC0_ping_PC5_RIP.png)

### R0配置标准ACL

```
在R0上配置标准ACL，禁止PC0 ping PC5,允许PC2 ping PC5,请思考需采用几条ACL，应用于R0那个端口、什么方向;配置完毕后，PC0 ping PC5显示什么信息？
```

#### 配置ACL

```
R0(config)# access-list 1 permit host 192.168.22.20			#允许主机192.168.22.20的数据包
R0(config)# access-list 1 deny any							#拒绝其他所有的数据包
```

#### 接口及方向

```
R0(config)# interface serial 0/3/0							#进入接口se0/3/0端口
R0(config-if)# ip access-group 1 out						#将指定的访问列表应用到se0/3/0接口的入方向
```

#### PC0  ping  PC5

![](https://www.zhengyuanyuan520.cn/images/switch/acl/PC0_ping_PC5_access-list.png)

#### PC0 PING PC3能通吗，为什么？ 

```
解析：PC0 不能ping通PC3，因为我们配置了标准acl，在R0的进方向就已经将PC0发出的数据包拒绝了，我们设置了在192.168.22.0/24中只允许192.168.22.20发出的数据，其他主机无法向外网发送数据。
```

#### PC2 ping PC5 能通吗，为什么？

```
PC2可以ping通PC5.因为我们写的acl配置就是运行主机PC2访问外网，而且由于之前我们写了RIP，保证了全网互通，所以PC2可以ping通PC5。
```

### R0配置拓展ACL

```
在R0上配置扩展ACL，禁止PC2访问服务器WEB服务，但是可以ping通服务器，请思考需采用几条ACL，应用于R0那个端口、什么方向;配置完毕后，PC0访问服务器WEB服务显示什么信息？
```

#### 配置ACL

```
R0(config)# access-list 101 deny tcp host 192.168.22.20 0.0.0.0 192.168.18.250 eq www 		#拒绝主机192.168.22.20向主机192.168.18.250的www请求
R0(config)# access-list 101 permit ip any any 			#允许访问列表101的任意IP通过控制列表
```

#### 端口及方向

```
R0(config)# interface fastEthernet 0/0				#进入Fa0/0端口
R0(config-if)# ip access-group 101 in				#将指定的访问列表应用到Fa0/0接口的入方向
--------------------------------------------------------------------------------------
解析：根据ACL的放置原则，拓展ACL应放置在尽可能靠近需要过滤的流量源的位置上，所以应该选择接口R0的Fa0/0接口。由于要检查的数据流是从接口Fa0/0流入的，所以检查方向为“in”。
```

#### PC0访问服务器WEB服务

![](https://www.zhengyuanyuan520.cn/images/switch/acl/PC2_to_WEB.png)

### 思考题

**对于标准型ACL，应该放在网络什么位置；而对于扩展型ACL，又应该放在网络什么位置？**

```
标准ACL不指定目的地址，所以其位置应该尽可能靠近目的地。
根据ACL的放置原则，拓展ACL应放置在尽可能靠近需要过滤的流量源的位置上。
```

**在IP访问列表中，如果到最后也没有找到匹配，则传输数据包将如何处理？（以cisco为例）**

```
如果都不匹配，那么一定匹配最后的隐含拒绝条目，思科默认拒绝。
```

**你该如何安排访问列表中条目顺序？**

```
①最小特权原则。只给受控对象完成任务所必需的最小的权限，因为总规则是各个规则的交集，只满足部分条件的是不容许通过的。
②最靠近受控对象原则。检查规则时是采用自上向下的形式在ACL中逐条检测的，只要发现符合条件的就立刻转发，不再继续检测后面的ACL语句。
③默认丢弃原则。如果都不匹配，那么一定匹配最后的隐含拒绝条目，思科默认拒绝。
④拓展ACL中具体的判别条目放在前面，标准ACL按照主机、网络、any排序。
```

