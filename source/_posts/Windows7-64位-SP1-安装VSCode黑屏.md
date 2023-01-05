title: Windows7 64位 SP1  安装VSCode黑屏
author: HaleyCH
tags:
  - windows7
  - vscode
  - .NET Framework
cover_image: 'http://i.hluvmiku.tech/f/63b187d80226d7a90750730d'
categories:
  - 疑难解答
abbrlink: 86e08dc7
date: 2023-01-01 20:54:00
---

![img_63b187d80226d7a90750730d](http://i.hluvmiku.tech/f/63b187d80226d7a90750730d/)
# 前言
给一台古早的 Windows7 64位 SP1 安装 VSCode 时遇到了种种问题，记录一下。


# 解决方案

~~我的评价是，不如用 [https://vscode.dev/](https://vscode.dev/)~~

首先我们要知道， `1.70.3` 版本的vscode是win7能用的最后一版。
![img_63b1837baf4452e2604c5b6e](http://i.hluvmiku.tech/f/63b1837baf4452e2604c5b6e/)
具体下哪个版本自己参考 [这里](https://code.visualstudio.com/docs/supporting/faq#_previous-release-versions) 。
总之选一个正确的版本 `https://update.code.visualstudio.com/{version}/win32-x64-archive/stable` 。

下载，一路 `next`，安装完了，启动，出现了黑黑的一个框。
1. 确定是否装了正确的`.NET Framework`。[下载界面](https://dotnet.microsoft.com/zh-cn/download/dotnet-framework)
没有或者安装版本过低（似乎过高也不行，4.5.2 最好）重新安装，重启。
[官方文档](https://learn.microsoft.com/zh-cn/dotnet/framework/migration-guide/how-to-determine-which-versions-are-installed)
2. 如果还黑屏，选中 `VScode`的快捷方式，右键， `属性` ,在 `目标` 的最后加上 ` --disable-gpu`，注意最前面有一个空格。如图所示，保存，运行。
![img_63b1866435ac386ff0cef91d](http://i.hluvmiku.tech/f/63b1866435ac386ff0cef91d/)
3. 如果还是黑屏， `属性->兼容性->以兼容模式运行这个程序` 。
4. 再有问题的话确定下你vscode的版本对不对，`.NET Framework` 版本对不对。然后重复1、2、3。

还是不行的话我也爱莫能助了。

# 参考资料
 - [https://learn.microsoft.com/zh-cn/dotnet/framework/migration-guide/how-to-determine-which-versions-are-installed](https://learn.microsoft.com/zh-cn/dotnet/framework/migration-guide/how-to-determine-which-versions-are-installed)