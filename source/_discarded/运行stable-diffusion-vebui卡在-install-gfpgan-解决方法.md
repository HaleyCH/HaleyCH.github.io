title: 运行stable-diffusion-vebui卡在 install gfpgan 解决方案
author: HaleyCH
tags:
  - Stable Diffusion
  - FAQ
categories:
  - Stable Diffusion
abbrlink: 4cd6152c
date: 2022-10-11 19:14:00
---
# 解决方案
1. 打开`launch.py`
2. 找到`gfpgan_package = os.environ.get('GFPGAN_PACKAGE', "git+https://github.com/TencentARC/GFPGAN.git@8d2447a2d918f8eba5a4a01463fd48e45126a379")`此行，将`https`改为`http`。
3. 若还是很慢，建议换个代理。

# 相关资源
- stable-diffusion-webui GitHub仓库地址：`https://github.com/AUTOMATIC1111/stable-diffusion-webui`