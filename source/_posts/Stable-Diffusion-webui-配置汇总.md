title: stable-diffusion-webui 快速部署（AI生成老婆）
author: HaleyCH
abbrlink: ee839213
tags:
  - 教程
  - Stable Diffusion
categories:
  - Stable Diffusion
cover_image: 'http://i.hluvmiku.tech/f/63b1485335ac386ff0cef905/'
date: 2022-10-11 18:45:00
---
# 相关资源
- stable-diffusion-webui GitHub仓库地址：
`https://github.com/AUTOMATIC1111/stable-diffusion-webui`
- Novel AI 泄露权重part.1 磁链：`magnet:?xt=urn:btih:5bde442da86265b670a3e5ea3163afad2c6f8ecc&dn=novelaileak&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2F9.rarbg.com%3A2810%2Fannounce&tr=udp%3A%2F%2Ftracker.openbittorrent.com%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.openbittorrent.com%3A80%2Fannounce&tr=udp%3A%2F%2Fopentracker.i2p.rocks%3A6969%2Fannounce`
- Novel AI 泄露权重part.2 磁链： `magnet:?xt=urn:btih:a20087e7807f28476dd7b0b2e0174981709d89cd&dn=novelaileakpt2&tr=udp%3A%2F%2Ftracker.openbittorrent.com%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.openbittorrent.com%3A80%2Fannounce&tr=https%3A%2F%2Ftracker.nanoha.org%3A443%2Fannounce`
- NAI中效果最好的权重 Google Drive：`https://drive.google.com/drive/folders/1tHya4XllthvxUcPPEZeJ896q9N0frxN0?usp=sharing`
- 傻瓜式Colab部署Notebook：`https://colab.research.google.com/drive/1Z2kCA5lUFYUvHJozUhqW9dxIVyOYDnLd?usp=sharing`
- 更多SDmodel：`https://rentry.org/sdmodels`


# 本地部署

## windows环境需求：
1. 安装python 3.10.6（但是经过我测试，安装3.9版本也可行，还能规避不少bug）。可选：使用[conda](https://docs.conda.io/en/latest/)安装
2. 安装[git](https://git-scm.com/download/win)
3. 配置CUDA，安装[11.3版本](https://developer.nvidia.com/cuda-11.3.0-download-archive)，并且配置[cuDNN](https://developer.nvidia.com/cudnn)

## 配置
1. 在想要下载的路径打开`cmd`使用`git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git`将SD-webui克隆至本地。
2. 下载所需权重，将其重命名为`model.ckpt`放入`models/Stable-diffusion/`下
3. 运行 `webui-user.bat`

## 远程访问
1. 新建`share.bat`
2. 在其中输入`python launch.py --share --gradio-debug --gradio-auth username:password`
3. 双击运行`share.bat`即可

# Colab部署

## 需求：
1. 一个Google账号
2. 可以访问colab的途径

## 配置
1. 将所需权重保存至`Google Drive`中
2. 访问`https://colab.research.google.com/drive/1Z2kCA5lUFYUvHJozUhqW9dxIVyOYDnLd?usp=sharing`
3. 从上到下依次执行代码