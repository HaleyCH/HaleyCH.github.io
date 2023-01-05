---
title: 在服务器上使用clash，解决服务器无法访问GitHub
author: HaleyCH
tags:
  - linux
  - clash
  - git
  - GitHub
cover_image: 'https://i.hluvmiku.tech/f/63b6e87cc65c09c012b31dac/'
categories:
  - 问题解决
abbrlink: 17ae7618
date: 2023-01-05 22:54:00
---
![img_63b6e87cc65c09c012b31dac](https://i.hluvmiku.tech/f/63b6e87cc65c09c012b31dac/)
# 前言

因为某些原因，Github在20222下半年某月开始无法正常访问，影响服务器正常备份。
于是乎，打算在服务器上运行clash连上去。

# 解决方案

1. 在[Clash Github Release](https://github.com/Dreamacro/clash/releases)页找到适合自己的版本，并解压。
![img_63b6e5ae895b35130a4ea4cc](https://i.hluvmiku.tech/f/63b6e5ae895b35130a4ea4cc/)

2. 准备clash配置文件 `config.yaml` ，可以参考之前写的 [在Clash中直接使用各种订阅链接](https://blog.hluvmiku.tech/posts/950e07ae/) 通过订阅链接获取配置文件。

3. 运行 ` ./clash-linux-amd64 -d . -f './config.yaml'`,它会先在下载 `Country.mmdb` 到当前目录,若无法正常下载，可以通过 [这里](https://static.hluvmiku.tech/download/Country.mmdy) 直接下载。
看到如下图界面代表成功运行：
![img_63b6e7659044e9b040a42ec9](https://i.hluvmiku.tech/f/63b6e7659044e9b040a42ec9/)

4. 配置 `git` ，使其通过代理访问。
```shell
git config --global https.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890
```
![img_63b6e827895b35130a4ea4ce](https://i.hluvmiku.tech/f/63b6e827895b35130a4ea4ce/)
看到访问Github成功。

5. 附：取消代理方法
```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```

# 参考资料

 - [https://github.com/Dreamacro/clash/wiki](https://github.com/Dreamacro/clash/wiki)
