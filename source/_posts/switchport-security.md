---
title: 交换机端口安全配置练习
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 网络安全
date: 2020-02-27 11:11:11
music:
  type: song  
  id: 1404885266
comments: true
tags:  
	- 网络安全
	- 交换机
	- 思科
---

实验用到的知识点：

1. 启用端口安全功能配置

2. 端口安全mac地址配置
3. 端口安全mac地址数目配置
4. 端口安全违规处理方式配置

<!-- more -->

## 任务

> 1. VLAN及VLAN间路由配置；
>
> 2. 端口安全应用配置：左边网络中只允许PC0接入C1，右边网络允许两个终端用户接入C1；

## 实现步骤

> 如图所示，二层结构构建的本地网络包括一个核心交换机和两个接入交换机，按图示要求为S1、S2划分VLAN及成员。



![](https://www.zhengyuanyuan520.cn/images/switch/switchport-security/photo1.png)



### 记录表格：

| 设备名 | 接口   | IP地址/掩码    | 网关地址       | 备注                |
| ------ | ------ | -------------- | -------------- | ------------------- |
| C1     | vlan 1 | 10.35.1.254/24 |                |                     |
| C1     | vlan 2 | 10.35.2.254/24 |                |                     |
| S1     | Fa0/1  |                |                | vlan 1              |
| S1     | Fa0/2  |                |                | vlan 2              |
| S1     | Fa0/3  |                |                | mac: 0001.96ce.1e03 |
| S2     | Fa0/1  |                |                | vlan 1              |
| S2     | Fa0/2  |                |                | vlan 2              |
| S2     | Fa0/3  |                |                | mac: 00e0.b086.8803 |
| PC0    |        | 10.35.1.1/24   | 10.35.1.254/24 | mac: 0060.7020.93BB |
| PC1    |        | 10.35.2.1/24   | 10.35.2.254/24 | mac: 0090.2150.050B |
| PC2    |        | 10.35.1.2/24   | 10.35.1.254/24 | mac: 0004.9A58.D178 |
| PC3    |        | 10.35.2.2/24   | 10.35.2.254/24 | mac: 0002.17B3.896B |

### 配置VLAN间路由

> 在S1、S2、C1进行设置，最终实现PC间的互Ping，各PC均可ssh C1

#### S1:  中继接口

```
S1(config)# vlan 2     						#创建vlan2
S1(config-vlan)# exit   					#回到全局模式
S1(config)# interface fastEthernet 0/2   	#进入2号接口
S1(config-if)# switchport mode access   	#定义端口工作模式为access
S1(config-if)# switchport access vlan 2		#将端口加入到vlan 2
S1(config-if)# exit							#回到全局模式
S1(config)# interface fastEthernet 0/3		#进入3号接口
S1(config-if)# switchport mode trunk		#定义端口工作模式为trunk
S1(config-if)# exit							#回到全局模式
```

#### S2: 中继接口

```
S2(config)# vlan 2     						#创建vlan2
S2(config-vlan)# exit   					#回到全局模式
S2(config)# interface fastEthernet 0/2   	#进入2号接口
S2(config-if)# switchport mode access   	#定义端口工作模式为access
S2(config-if)# switchport access vlan 2		#将端口加入到vlan 2
S2(config-if)# exit							#回到全局模式
S2(config)# interface fastEthernet 0/3		#进入3号接口
S2(config-if)# switchport mode trunk		#定义端口工作模式为trunk
S2(config-if)# exit							#回到全局模式
```

#### C1：SSH

> 主机名C1、域名wtctx、用户名、密码均为txXX、enable不加密密码tx18XX（XX为学号最后2位）

```
C1(config)# hostname C1						#设置主机名为C1
C1(config)# ip domain-name wtctx			#设置域名为wtctx
C1(config)# crypto key generate rsa			#生成rsa秘钥
C1(config)# line vty 0 15					#进vty接口，最多15人同时在线
C1(config-line)# transport input ssh		#启用SSH登录
C1(config-line)# privilege level 15			#设置用户操作等级为最高级
C1(config-line)# login local				#使用本地验证
C1(config-line)# exit						#回退到全局模式
C1(config)# username tx11 password tx11		#创建用户tx11，密码为tx11
C1(config)# enable password tx1811			#设置enable明文密码
```

#### C1：中继接口

```
C1(config)# interface range fastEthernet 0/1-2			#进入0/1和0/2端口
C1(config-if)# switchport trunk encapsulation dot1q		#封装vlan帧
C1(config-if)# switchport mode trunk					#定义接口工作模式
C1(config-if)# exit										#退出端口
```

#### C1：开启路由功能

```
C1(config)# ip routing		#开启路由功能
```

#### C1：设置各VLAN网关地址

> 地址为该网段最大主机地址（注意VLAN接口默认关闭且手工打开）

```
C1(config)# vlan 2										#创建vlan 2
C1(config-vlan)# exit									#退回到全局模式
C1(config)# interface vlan 1							#进入vlan1接口
C1(config-if)# ip address 10.35.1.254 255.255.255.0		#配置IP和子网掩码
C1(config-if)# no shutdown								#接口启用
C1(config-if)# exit										#退出vlan1接口
C1(config)# interface vlan 2							#进入vlan2接口
C1(config-if)# ip address 10.35.2.254 255.255.255.0		#配置IP和子网掩码
C1(config-if)# exit										#退出vlan2接口
```

#### 记录结果

> 为各PC设置网关地址，设置完毕PC0 分别ping PC1 和PC2，记录结果。



![](https://www.zhengyuanyuan520.cn/images/switch/switchport-security/photo2.png)



### 端口安全配置。

#### C1：fa0/1开启安全端口功能

> 配置时建议关闭端口，关闭端口可清空mac地址表

```
C1(config)# interface fastEthernet 0/1		#进入Fa0/1接口
C1(config-if)# shutdown						#关闭端口
C1(config-if)# switchport port-security		#开启安全端口功能
```

#### C1：fa0/1安全端口禁用DTP

```
C1(config-if)# switchport nonegotiate		#禁用DTP
```

#### C1：fa0/1安全端口允许最大地址数

```
C1(config-if)# switchport port-security maximum 3		#设置允许最大地址数
------------------------------------------------------------------------
解析：C1从Fa0/1学习地址时会优先学习与之直连的接口地址（即S1交换机的Fa0/3端口），C1上有两个VLAN对应两条，加上静态指定的共有三条；
```

#### C1：fa0/1安全端口指定允许接入的地址

```
C1(config-if)# switchport port-security mac-address 0060.7020.93BB
```

#### C1：fa0/1安全端口指定违规处理行为

> 建议使用protected，思考为什么

```
C1(config-if)# switchport port-security violation protect
------------------------------------------------------------------------
解析：违规方式采用protect是为了确保网络能为合规的数据提供继续的服务，若采用默认方式，违规后端口将自动关闭，从而导致网络不可用。
```

#### C1：fa0/2开启安全端口功能

> 配置时建议关闭端口，关闭端口可清空mac地址表

```
C1(config-if)# no shutdown						#开启Fa0/1端口
C1(config-if)# exit								#退出Fa0/1端口
C1(config)# interface fastEthernet 0/2			#进入Fa0/2端口
C1(config-if)# shutdown							#关闭Fa0/2端口
C1(config-if)# switchport port-security			#开启安全端口功能
```

#### C1：fa0/2安全端口禁用DTP

```
C1(config-if)# switchport nonegotiate			#禁用DTP
```

#### C1：fa0/2安全端口允许最大地址数

> 思考数值设置多少合理，依据是什么

```
C1(config-if)# switchport port-security maximum 5		#设置允许最大地址数
------------------------------------------------------------------------
解析：C1会粘滞5个来自Fa0/2的mac地址记录，分别是从Fa0/1学习地址时会优先学习与之直连的接口地址（即S1交换机的Fa0/3端口），vlan1和vlan2接口的mac地址，PC2和PC3的mac地址。
```

#### C1：fa0/2安全端口采用地址粘滞功能

```
C1(config-if)# switchport port-security mac-address sticky
```

#### C1：fa0/2安全端口指定违规处理行为

> 建议使用protected，思考为什么

```
C1(config-if)# switchport port-security violation protect
------------------------------------------------------------------------
解析：违规方式采用protect是为了确保网络能为合规的数据提供继续的服务，若采用默认方式，违规后端口将自动关闭，从而导致网络不可用。
```

#### 记录结果

> 设置完毕PC0 分别ping PC1 和PC2，记录结果，思考原因



![](https://www.zhengyuanyuan520.cn/images/switch/switchport-security/photo3.png)



```
解析：虽然已经做到了全网互通，但是由于PC1没有设置允许它接入，且设置了保护模式为protect，所以PC1的数据流量对于交换机来说是违规的，端口对PC1的数据进行丢弃，所以PC0的数据无法发送给PC1。
```

### 思考

![](https://www.zhengyuanyuan520.cn/images/switch/switchport-security/photo4.png)

```
解析：此时mac地址表会出现共5个来自Fa0/2的mac地址记录，分别是从Fa0/1学习地址时会优先学习与之直连的接口地址（即S1交换机的Fa0/3端口），vlan1和vlan2接口的mac地址，PC2和PC3的mac地址。
```

