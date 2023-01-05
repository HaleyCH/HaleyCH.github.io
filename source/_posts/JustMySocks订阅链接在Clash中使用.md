title: 在Clash中直接使用JustMySocks订阅链接
author: HaleyCH
tags:
  - clash
  - justmysocks
cover_image: 'http://i.hluvmiku.tech/f/63b14be135ac386ff0cef907/'
categories:
  - 互联网
abbrlink: 950e07ae
date: 2023-01-01 17:00:00
---
# 前言

在使用`JustMySocks`订阅链接时，发现直接下载下来是`base64`格式，而且解码后是各种订阅链接，不方便`clash`直接使用。
查询Github后发现一个挺好用的库[subconverter](https://github.com/tindy2013/subconverter)。
部署好后直接可以按照readme所说使用。
（实际上它可以支持好多好多格式转换，结尾附表。）

# 解决方案

__我自己部署了一个，顺带写了一个简易的前端，可以直接使用，后端就是`subconverter`，不会保存任何记录。
[传送门](!http://sub.hluvmiku.tech/) 在这。__

若不放心，想在本地部署，可以按照以下步骤：
 
1. 在[Release](https://github.com/tindy2013/subconverter/releases)中找到所需的版本。

2. 以Linux为例，`tar -zxvf release.tar.gz` 后进入目录，执行 `bash ./subconverter` 即可。看到下图所示输出代表部署成功。默认端口`25500`。
![img_63b14f6335ac386ff0cef90d](http://i.hluvmiku.tech/f/63b14f6335ac386ff0cef90d/)

3. 按照[Readme](https://github.com/tindy2013/subconverter/blob/master/README.md)所说进行调用。快速使用：`http://127.0.0.1:25500/sub?target=%TARGET%&url=%URL%`。
比如你的订阅链接是`http://a@bcd-1.com/sub?token=233`,目标类型是`Clash`，那新订阅链接就是`http://127.0.0.1:25500/sub?url=http%3A%2F%2Fa%40bcd-1.com%2Fsub%3Ftoken%3D233?target=clash`。__注意要对url进行URLencode。
可以采用 [我写的前端](http://sub.hluvmiku.tech/en/) 快速转化（纯前端，不涉及任何后端交互），域名就自己改改好了。
![img_63b1516d0226d7a907507303](http://i.hluvmiku.tech/f/63b1516d0226d7a907507303/)

4. 将新的订阅链接丢进clash里，更新，看到类似下图所示代表成功。

![img_63b14c0c35ac386ff0cef909](http://i.hluvmiku.tech/f/63b14c0c35ac386ff0cef909/)

*更多高级设置参考[Readme](https://github.com/tindy2013/subconverter/blob/master/README.md)。*


# 附：转换列表

| Type         | As Source  | As Target    | Target Name |
| ------------ | :--------: | :----------: | ----------- |
| Clash        |     ✓      |      ✓       | clash       |
| ClashR       |     ✓      |      ✓       | clashr      |
| Quantumult   |     ✓      |      ✓       | quan        |
| Quantumult X |     ✓      |      ✓       | quanx       |
| Loon         |     ✓      |      ✓       | loon        |
| SS (SIP002)  |     ✓      |      ✓       | ss          |
| SS Android   |     ✓      |      ✓       | sssub       |
| SSD          |     ✓      |      ✓       | ssd         |
| SSR          |     ✓      |      ✓       | ssr         |
| Surfboard    |     ✓      |      ✓       | surfboard   |
| Surge 2      |     ✓      |      ✓       | surge&ver=2 |
| Surge 3      |     ✓      |      ✓       | surge&ver=3 |
| Surge 4      |     ✓      |      ✓       | surge&ver=4 |
| V2Ray        |     ✓      |      ✓       | v2ray       |
| Telegram-liked HTTP/Socks 5 links |     ✓      |      ×       | Only as source |