---
title: 思科交换机开启ssh远程
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 网络安全
date: 2020-02-24 17:52:30
comments: true
tags:  
	- 网络安全
	- 交换机
	- 思科
---

由于传统的telnet方式使用明文的方式进行密码和数据的传送，对于安全性我们无法得到保障，那么接下来介绍一下通过ssh方式远程，ssh方式使用了加密的方式进行密码和数据的传输，提高了网络设备的安全性。
<!-- more -->

## 配置IP

    Switch> enable     #进入管理员模式
    Switch# config terminal   #进入全局模式
    Switch(config)# interface vlan 1   #进入vlan1接口
    Switch(config)# ip address 192.168.0.1 255.255.255.0    #配置IP地址和子网掩码
    Switch(config)# no shutdown    #启用vlan 1接口

## 修改主机名

	Switch(config)# hostname MS1   #修改交换机的主机名，后期配置域名的主机名

## 配置域名

	MS1(config)# ip domain-name qinhao.com   #配置域名

## 生成rsa秘钥

    MS1(config)# crypto key generate rsa   #生成rsa秘钥，默认长度为512，建议修改为1024

## 定义ssh远程的线路

    MS1(config)# line vty 0  15  #进入vty端口模式
    MS1(config)# transport input ssh 
    MS1(config)# privilege level 15
    MS1(config)# login local

## 创建本地用户

    MS1(config)# username qinhao password zyy520

## 设置enable登录密码

    MS1(config)# enable secret 123456   #进入管理员模式需要的密码

## PC0通过ssh远程连接MS1

    pc> ssh -l qinhao 192.168.0.1		#ssh用法：ssh -l 用户名 IP地址
    open	#会提示我们开启
    Password: zyy520	#输入ssh用户的密码
