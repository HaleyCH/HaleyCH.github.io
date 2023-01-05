title: Hexo-Admin配置封面
author: HaleyCH
tags:
  - hexo
  - hexo-admin
categories:
  - 博客搭建
cover_image: 'http://i.hluvmiku.tech/f/63b17afc35ac386ff0cef919/'
abbrlink: '231978e2'
date: 2023-01-01 18:59:00
---
# 前言

配置完 `Hexo-Admin` 后，博客是默认没有封面的。
但我们可以在 `_config.yml` 中设置，使其具有封面。

*Hexo-Admin 安装可以看我的上一篇博客。[传送门](http://blog.hluvmiku.tech/posts/ab7d428c/)*

# 解决方法

1. 查看你的主题中封面对应的metadata，这里以我用的 `cupertino` 主题为例。
进入 `hexo/themes/cupertino/layout/`。 找到主页对应的主题文件，通常是 `index.ejs` 。

2. 查找 `cover` ，可以看到，我这里封面对应的metadata是 `cover_image` 。
![img_63b1698835ac386ff0cef915](http://i.hluvmiku.tech/f/63b1698835ac386ff0cef915/)

3. 在 `hexo/_config.yml` 的最后加上：
```yaml
metadata:
  <your cover metadata>:
``` 
![img_63b16a4535ac386ff0cef917](http://i.hluvmiku.tech/f/63b16a4535ac386ff0cef917/)
需要注意编辑的是hexo根目录下的 `_config.yml` 而不是主题下的。

4. 重启hexo `hexo s`,进入 `Hexo-Admin` ，点击设置，若看到类似下图界面则成功。
![img_63b16b20af4452e2604c5b68](http://i.hluvmiku.tech/f/63b16b20af4452e2604c5b68/)

# 参考资料
- [https://github.com/jaredly/hexo-admin/issues/144](https://github.com/jaredly/hexo-admin/issues/144)
- [https://github.com/jaredly/hexo-admin#custom-post-metadata](https://github.com/jaredly/hexo-admin#custom-post-metadata)