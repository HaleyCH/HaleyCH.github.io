title: Hexo-Admin安装与简易配置
author: HaleyCH
tags:
  - hexo
  - hexo-admin
categories:
  - 博客搭建
cover_image: 'http://i.hluvmiku.tech/f/63b166c035ac386ff0cef913/'
abbrlink: ab7d428c
date: 2023-01-01 18:38:00
---
![img_63b166c035ac386ff0cef913](http://i.hluvmiku.tech/f/63b166c035ac386ff0cef913/)
# 前言

>Hexo是一个快速、简洁且高效的博客框架。 `npm install hexo-cli -g.`

将Hexo部署到服务器后，编辑MD文件同步变得比较麻烦。
而`Hexo-Admin`作为一个Hexo的MD在线编辑工具则解决了这一问题。

# 安装

1. `cd path/to/hexo` 进入hexo目录
2. `npm install --save hexo-admin`
3. 启动hexo `hexo s`

访问 `http://localhost:4000/admin/` 看到类似下图界面说明成功安装。

![img_63b1649f35ac386ff0cef90f](http://i.hluvmiku.tech/f/63b1649f35ac386ff0cef90f/)

# 简易配置

在完成上述步骤后，任何人都可以直接访问admin后台，需要设置密码。

1. 如图所示点击 `Settings->Setup authentification here` 
![img_63b165450226d7a907507305](http://i.hluvmiku.tech/f/63b165450226d7a907507305/)

2. 填写完用户名、密码、secret后将生成的代码复制到 `_config.yml` 中保存。
![img_63b165b635ac386ff0cef911](http://i.hluvmiku.tech/f/63b165b635ac386ff0cef911/)
保存后 `_config.yml` 差不多长这样：
![img_63b16632af4452e2604c5b66](http://i.hluvmiku.tech/f/63b16632af4452e2604c5b66/)

3. 重启Hexo `hexo s`


# 参考资料
- [https://hexo.io/zh-cn/](!https://hexo.io/zh-cn/)
- [https://albenw.github.io/posts/4ffa5bc6/](!https://albenw.github.io/posts/4ffa5bc6/)