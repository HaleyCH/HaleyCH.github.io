title: CentOS 7.9 + Hexo 快速搭建博客
author: HaleyCH
abbrlink: 14a41c44
tags:
  - 教程
categories:
  - Blog搭建
date: 2022-09-05 19:45:00
---
本文讲述了基于`CentOS 7.9 + Hexo`的个人博客搭建。
## 1.环境配置
1. 更新包： `yum upgrade`
2. 安装`screen`以避免ssh窗口关闭时终止博客进程：`yum install screen -y`
3. 安装`Hexo`：`yum install hexo`
4. 安装`Git`以便后续主题配置以及版本控制：`yum install git -y`
5. 配置`filezilla`：`yum install epel-release -y`，并开放`22`端口：`firewall-cmd --zone public --add-port 22 --permanent`。最后重启防火墙：`systemctl restart firewalld.service`。

## 2.Hexo配置
### 2.1 博客项目创建
1. 新建一个窗口`screen -S blog`（关于`screen`有关操作可参考[这篇博客](https://www.cnblogs.com/mchina/archive/2013/01/30/2880680.html)）
## 3.防火墙配置


## 4.域名解析

## 5.Hexo 主题挑选