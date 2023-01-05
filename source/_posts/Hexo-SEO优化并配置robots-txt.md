title: Hexo SEO优化并配置robots.txt
author: HaleyCH
abbrlink: 71e799ed
tags:
  - Blog
categories:
  - 博客搭建
cover_image: 'http://i.hluvmiku.tech/f/63b147b4af4452e2604c5b64/'
date: 2022-09-10 13:14:00
---
闲来无事搭了个Hexo博客，为了使其能在百度、谷歌等搜索引擎能被搜索到，打算对其进行SEO优化。毕竟没法被搜到的博客也就只能图个自娱自乐。
# sitemap配置
>sitemap 可方便网站管理员通知搜索引擎，他们网站上有哪些可供抓取的网页。

因此 在使得网站被搜索引擎爬取之前，有必要创建`sitemap`。
以下为`Hexo`快速配置方法:
1. 安装相关插件
```
npm install hexo-generator-sitemap --save
npm install hexo-generator-baidu-sitemap --save
``` 
2. 重新生成静态网站`hexo clean && hexo g && hexo h`。


这样便能在`public`目录下生成`sitemap.xml`与`baidu_sitemap.xml`了。

# Hexo robots.txt配置
1. 进入Hexo博客目录中`public`文件夹下，若无该文件夹使用`hexo g`命令生成。
2. 在`public`文件夹下创建`robots.txt` : `vim robots.txt`

本博客中robots.txt如下配置(域名还在备案中，故暂时用公网IP代替):
```
User-agent: *
Allow: /
Allow: /archives/
Allow: /categories/
Allow: /tags/
Allow: /about/
Disallow: /admin/
Disallow: /css/
Disallow: /theme-img/
Sitemap: http://47.97.118.189/sitemap.xml
Sitemap: http://47.97.118.189/baidu_sitemap.xml
```

**配置完这二者过大约一天即可在搜索引擎上查找到自己的博客了**


# 何为robots.txt
简单的引用wiki中的[原文](https://zh.m.wikipedia.org/zh-hans/Robots.txt)。

>robots.txt（统一小写）是一种存放于网站根目录下的ASCII编码的文本文件，它通常告诉网络搜索引擎的漫游器（又称网络蜘蛛），此网站中的哪些内容是不应被搜索引擎的漫游器获取的，哪些是可以被漫游器获取的。因为一些系统中的URL是大小写敏感的，所以robots.txt的文件名应统一为小写。robots.txt应放置于网站的根目录下。如果想单独定义搜索引擎的漫游器访问子目录时的行为，那么可以将自定的设置合并到根目录下的robots.txt，或者使用robots元数据（Metadata，又称元资料）。

当然，使用robots元数据也可以实现类似的效果：`<meta name="robots" content="noindex,nofollow" />`。

*需要注意的是robots.txt与robots元数据是约定俗成的，并不能有效保护隐私。*
# robots.txt具体语法
具体语法十分简单(以谷歌为例)：

>·user-agent: [必需，每个组需含一个或多个 User-agent 条目] 该指令指定了规则适用的自动客户端（即搜索引擎抓取工具）的名称。这是每个规则组的首行内容。Google 用户代理列表中列出了 Google 用户代理名称。 使用星号 (*) 会匹配除各种 AdsBot 抓取工具之外的所有抓取工具，AdsBot 抓取工具必须明确指定。例如：
>#- Example 1: Block only Googlebot
User-agent: Googlebot
Disallow: /
>
>#- Example 2: Block Googlebot and Adsbot
User-agent: Googlebot
User-agent: AdsBot-Google
Disallow: /
>
>·disallow: [每条规则需含至少一个或多个 disallow 或 allow 条目] 您不希望用户代理抓取的目录或网页（相对于根网域而言）。如果规则引用了某个网页，则必须提供浏览器中显示的完整网页名称。它必须以 / 字符开头；如果它引用了某个目录，则必须以 / 标记结尾。
>
>·allow: [每条规则需含至少一个或多个 disallow 或 allow 条目] 上文中提到的用户代理可以抓取的目录或网页（相对于根网域而言）。此指令用于替换 disallow 指令，从而允许抓取已禁止访问的目录中的子目录或网页。对于单个网页，请指定浏览器中显示的完整网页名称。对于目录，请用 / 标记结束规则。
>
>·sitemap: [可选，每个文件可含零个或多个 sitemap 条目] 相应网站的站点地图的位置。站点地图网址必须是完全限定的网址；Google 不会假定存在或检查是否存在 http、https、www、非 www 网址变体。站点地图是一种用于指示 Google 应抓取哪些内容的理想方式，但并不用于指示 Google 可以抓取或不能抓取哪些内容。详细了解站点地图。