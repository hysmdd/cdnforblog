---
title: MySQL 8数据库基础
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: 数据库
date: 2020-02-27 12:50:11
comments: true
tags:  
	- 数据库
	- MySQL
---

MySQL基础语法，学习时做的笔记。

<!-- more -->



## 常用数据库命令

```mysql
create database 数据库名称;           	    //创建数据库
drop  database  数据库名称;					//删除数据库
show databases;							   //查看数据库
use 数据库名;								//使用数据库
```

## 更改加密方式

```mysql
 ALTER USER'root'@'localhost' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER;
 ALTER USER'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
 FLUSH PRIVILEGES;
```

## 创建学生表

```mysql
CREATE TABLE  表名称(
	列表名1  数据类型  [约束],
    列表名2  数据类型  [约束],
    ...
    列表名n  数据类型  [约束]
);
```

## 添加一列

```mysql
ALTER TABLE 表名称  ADD 列表名  数据类型;
```

## 修改一个表的字段类型

```mysql
alter table 表名称 modify  修改的列表名 数据类型(长度);
```

## 查看表结构

```mysql
desc  表名称;
```

## 修改表名称

```mysql
RENAME TABLE 原始表名称  TO  要修改成的表名称;
```

## 修改字符集

```mysql
ALTER TABLE 表名称  CHARACTER  SET 字符集名称;
```

## 修改表的列名

```mysql
ALTER TABLE 表名称  CHANGE  原始列名  新列名  数据类型;
```

## 注释

```mysql
#
```

## 查看表的字段信息

```mysql
desc 表名称;
```

## 删除一列：

```mysql
ALTER TABLE 表名称 DROP 字段名称;
```

## 删除表

```mysql
DROP TABLE 表名称;
```

