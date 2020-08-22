
# 						 	HP交换机配置

## 连接交换机的方法：

### 本地连接：

1. 使用配置线连接电脑

2. 查看对应的端口（方法：计算机右键---->管理---->系统工具---->设备管理器---->端口，查看对应的端口）

   ![查看对应端口](https://zhengyuanyuan520.cn/images/20191206/photo1.png)

3. 打开CRT软件,选择快速连接![选择快速链接](https://zhengyuanyuan520.cn/images/20191206/photo2.png)

4. 弹出的窗口中选择一下配置：

   ```文本
   协议：Serial
   端口：COM XX  (选择上面查到的端口号)
   波特率：9600
   流控：全部不选择
   其它不需要修改，点击连接即可
   ```

###  远程连接

1. win  + ｒ

2. 输入cmd，回车运行。

3. 远程功能的语法：

   ```
   telnet   IP地址
   ```

4. 输入用户名和密码登录远程交换机

   ```
   Username：此处输入用户名
   Password：此处输入密码
   ```

## 配置命令

1.进入管理员模式，默认登录是游客登录，需要使用命令进入管理员模式进行更多操作。#代表进入了管理员模式

```
enable
```

![进管理员模式](https://zhengyuanyuan520.cn/images/20191206/photo3.png)

2.进入全局模式。只有进入了全局模式，我们才可以对交换机的配置进行修改。

```文本
configure
```

![进入全局模式](https://zhengyuanyuan520.cn/images/20191206/photo4.png)

3.更换交换机的名称：

```
hostname  需要更换的名称
```

4.重启交换机：

```
reload
```

5.设置交换机远程登录的用户名以及密码：

```
设置用户名语法：password  manager  username  设置的远程登录用户名
```

![设置用户名](https://zhengyuanyuan520.cn/images/20191206/photo5.png)

![设置密码](https://zhengyuanyuan520.cn/images/20191206/photo6.png)

6.保存配置命令：

```
write  memory
```

7.添加vlan。前提是进入了配置模式。

```
vlan  端口号
```

8.配置管理IP，vlan  2000是管理vlan。

​	家属区、西区宿舍区以及办公区：10.10.102段

​	东区学生区多为：10.10.101段

​	vlan一般设置了untagged就必须设置对应的tagged口，否则会出现无法正常通信等故障。

```
vlan 2000
ip address IP地址
```

9.查看交换机的配置。既然添加了配置，我们就需要查看配置，看看我们是否添加成功。

```
show  run
```

10.静态路由。配置交换机一定要配置静态路由，否则会造成无法远程等故障。

```
ip  route  IP地址
```

11.修改支持的默认vlan数，修改后需要重启才可使用：

```
max-vlans  数字
```

12.查看端口的连接情况：

```
show  interface  brief
```

13.tagged与untagged。交换机连接电脑的端口设置为untagged端口，交换机与交换机之间的端口设为tagged端口。设置untagged与tagged需要进入vlan里面进行配置。

```
练习：A交换机的25号口上面接的是B交换机(汇聚)的13号口，我应该怎么配置才能保证可以上网呢？
```

14.端口隔离。端口隔离是为了实现[报文](https://baike.baidu.com/item/报文/3164352)之间的二层隔离，可以将不同的端口加入不同的VLAN，但会浪费有限的VLAN资源。采用端口隔离特性，可以实现同一VLAN内端口之间的隔离。用户只需要将端口加入到隔离组中，就可以实现隔离组内端口之间二层数据的隔离。端口隔离功能为用户提供了更安全、更灵活的组网方案。

```
filter source-port  "端口号"  drop  隔离的端口号  
```

15.查看邻居：

```
show  lldp  info  remote-device
```

16.删除vlan

```
no vlan  [vlan号码]
```

17.清空交换机配置：

```
erase  startup-config
```