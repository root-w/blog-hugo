---
date: 2016-07-25T11:10:08+08:00
isCJKLanguage: "true"
description: ""
tags:
- development
- mysql
- 效率
title: mysqlsandbox 的安装与使用
topics:
- Development
url: "mysql-sandbox-usage"
---


## 说明
官网：http://mysqlsandbox.net/

用途：

## 安装

方便快捷迅速的在一台机器上搭建 mysql 实例，包括：单个 mysql 实例，主从复制的 mysql 实例，和mysql 多实例，对于测试非常方便
具体安装使用请参照官网，在使用时碰到了两个问题，

1. Can't locate ExtUtils/MakeMaker.pm in @INC

	解决办法：`yum install perl-ExtUtils-CBuilder perl-ExtUtils-MakeMaker`

2. 使用异常，不论是执行 `make_replication_sandbox`，还是`make_replication_sandbox` 都提示以下信息：
> Use of uninitialized value $ENV{"USER"} in concatenation (.) or string at /usr/local/share/perl5/MySQL/Sandbox/Scripts.pm line 68.
installing and starting master


	解决方法：设置环境变量 USER

##  使用
###  使用 gtid 的主从复制
`make_replication_sandbox` 建立复制集群时，指定 `--gtid` 并不生效,需要在建立复制后，使用 enable_gtid 命令工具使集群使用 gtid

另外 `check_slave` 的输出是如下：

![check_slave](media/check_slave.png)，
并不会显示出 gtid 的信息，因此查看 slave 的复制情况仍然需要需要连入 mysql 查看况


