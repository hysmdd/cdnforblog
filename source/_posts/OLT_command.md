---
title: OLT基础命令
author:
    name: 覃浩
    avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
    url: https://www.zhengyuanyuan520.com
categories: 交换机
date: 2020-02-27 12:13:14
music:
  type: song  
  id: 554241732
comments: true
tags: 交换机
keywords: 交换机
description: 
photos: https://zhengyuanyuan520.cn/images/blog_background.jpg
---


适用于华为OLT的基础命令，这是当时学习时做的笔记。
<!-- more -->



## 1、基础命令模式功能及特性列表

| 命令模式     | 功能                     | 模式提示符实例  | 命令       |
| ------------ | ------------------------ | --------------- | ---------- |
| 普通用户模式 | 查看系统基本信息         | huawei>         | 登录后进入 |
| 特权模式     | 进行系统基本配置         | huawei#         | enable     |
| 全局配置模式 | 配置系统设备及全局性参数 | huawei(config)# | config     |

## 2、基础命令

- **查看ONU相关信息**

```
命令语法：display onu nat information

命令功能：用于查询通过OLT代理管理的ONU设备相关信息，包括ONU的公网IP地址，管理通道的VLAN ID以及ONU上行SNMP报文的优先级；以及ONU私网IP地址池的起始IP地址和范围。
```

- **配置ONU管理通道的VLAN**

```
命令语法：onu nat vlan vlanid

命令功能：配置VLAN ID的前提是OLT通过NAT代理管理ONU功能为使能状态。配置的目的是用于xPON单板根据此VLAN ID抓取ONU报文。

参数说明：
vlanid：设置ONU所属的代理管理通道的VLAN ID。其取值为数值类型，范围：2-4093。
```

- **对以太网接口进行配置**

```
命令语法：interface eth frameid/slotid

命令功能：此命令用于从全局配置模式进入到ETH模式。当需要在ETH模式下配置以太网口时，使用此命令。

参数说明：
frameid/slotid：用于标识机框号/槽位号。“/”需原样输入。当需要对某一指定槽位下发命令时使用此参数。
```

- **对GPON端口进行配置**

```
命令语法：interface gpon frameid/slotid

命令功能：此命令用于从全局配置模式进入到GPON模式。当需要在GPON模式下对GPON端口进行配置时，使用此命令。

参数说明：
frameid/slotid：用于标识机框号/槽位号。“/”需原样输入。当需要对某一指定槽位下发命令时使用此参数。
```

- **对管理网口进行配置**

```
命令语法：interface meth number

命令功能：此命令用于从全局配置模式进入到METH模式。进入METH模式后，可以配置维护网口的IP地址、Firewall以及接口的速率和双工状态等参数。

参数说明：
number：维护网口的编号，固定为0。number取数值类型，取值范围：0。
```

- **创建VLANIF接口并进入VLANIF模式**

```
命令语法：interface vlanif vlan-id

命令功能：interface vlanif命令用于从全局配置模式创建VLANIF接口并进入VLANIF模式。在VLANIF模式下，可以对虚拟的三层接口进行DHCP、防火墙、IP地址、MPLS、DHCP server、ARP等相关配置。

参数说明：
vlan-id：VLAN ID，输入的VLAN ID必须已经存在。取值类型为数值类型，取值范围：1-4093。
```

- **删除VLANIF接口**

```
命令语法：undo interface vlanif vlan-id

命令功能：undo interface vlanif命令用于删除指定的VLANIF接口。当系统中没有创建VLANIF接口时，无法执行此命令。

参数说明：
undo interface vlanif：命令的执行交互界面中仅显示已经创建VLANIF接口的VLAN ID。
```

- **回退至前一级模式**

```
命令语法：quit

命令功能：从当前模式（除Rsa-public-key模式、Rsa-key-code模式外的任何模式）退回到前一级模式或者退出配置环境。
```

- **一次性退回特权模式**

```
命令语法：return

命令功能：从当前模式（除普通用户模式、特权模式、Rsa-public-key模式、Rsa-key-code模式、Security模式之外的任何模式）“一次性”退回到特权模式。
```

- **设置OLT通过NAT代理管理ONU设备功能的状态**

```
命令语法：onu nat { enable | disable }

命令功能：此命令用于设置OLT通过NAT代理管理ONU设备功能的状态。当该功能为使能状态时，可以通过OLT代理管理ONU设备；当该功能为去使能状态时，不能通过OLT代理管理ONU设备，并且该功能去使能以后会终止业务引发用户配置信息会丢失，下次开关使能后需要重新配置UDP端口号等分配信息。
```

- **设置网络侧UDP起始端口号**

```
命令语法：onu nat base-port port-number

命令功能：此命令用于在ONU代理模式下，设置网络侧的UDP起始端口号。

参数说明：
port-number：UDP起始端口号。数值类型，取值范围：0-30720。缺省值：10000。
```

- **配置ONU的公网IP地址**

```
命令语法：onu nat ip ip-addr 

命令功能：此命令用于在使能OLT通过NAT代理管理ONU设备的功能时，配置ONU的公网IP地址。由于网管对ONU设备的查询和设置是基于公网IP地址的，在采取了OLT代理管理ONU设备的方式以后，网管看不到ONU的私网IP地址。因而，需要给ONU设备设置公网IP地址，便于实现网管通过ONU公网IP地址查询ONU的信息。

参数说明：
ip ip-addr：配置全局IP地址，点分十进制形式，且配置以后不许改变。此IP地址是单播IP地址。IP地址采用点分十进制，取值范围：0.0.0.0-255.255.255.255。缺省值：10.10.10.10
```

- **配置ONU的私网IP地址池的起始IP地址和范围**

```
命令语法：onu nat ip-pool { start-address ip-addr scope scope-value } 

命令功能：此命令用于在去使能OLT通过NAT代理管理ONU设备的功能时，配置ONU的私网IP地址池的起始IP地址和范围，支持用户根据实际情况配置ONU的私网IP地址和IP地址的个数。

参数说明：
start-address ip-addr ：配置ONU私网IP地址池的起始IP地址，点分十进制形式。此IP地址是单播IP地址。IP地址采用点分十进制，取值范围：0.0.0.0-255.255.255.255。缺省值：10.0.0.0。
scope scope-value ：配置ONU私网IP地址池的范围，也就是用户指定的IP的个数。数值类型，取值范围：1024-5120。缺省值：5120。

```

- **设置ONU上行SNMP报文的优先级。**

```
命令语法：onu nat priority priority-value

命令功能：onu nat priority命令用于使能OLT通过NAT代理管理ONU功能时，配置ONU上行SNMP报文的优先级。

参数说明：
priority priority-value ：设置ONU上行SNMP报文的优先级。数值类型，取值范围：0-7。默认值：7
```

- **配置ONU管理通道的VLAN  ID**

```
命令语法：onu nat vlan

命令功能：此命令用于使能OLT通过NAT代理管理ONU功能时，配置ONU管理通道的VLAN ID。配置ONU管理通道的VLAN ID主要用于xPON单板通过VLANID抓取ONU报文。

参数说明：
vlan vlanid ：设置ONU所属的代理管理通道的VLAN ID。数值类型，取值范围：2-4093。
```

