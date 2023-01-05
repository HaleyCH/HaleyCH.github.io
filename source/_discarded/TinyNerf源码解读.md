title: TinyNerf源码解读
author: HaleyCH
abbrlink: b430a095
tags: []
categories: []
date: 2022-09-10 15:20:00
---
因课业要求，开始自学`NeRF`算法。但是由于`NeRF`算法相对复杂一点，便打算从更加直观的`TinyNeRF`学起。([TinyNeRF](https://github.com/bmild/nerf/blob/master/tiny_nerf.ipynb)源码）

*本文解读的Bmild的TinyNeRF是TensorFlow版本*

# 前置知识

在`TinyNeRF`中，涉及到的知识点如下：

- Novel View Synthesis（新视角合成）
- Positional Encoding （位置编码）
- Multilayer Perceptron （MLP,多层感知机）
- Volume Rendering（体积渲染）

## Novel View Synthesis
对于这部分我并不是很熟悉，可参考[这篇](https://zhuanlan.zhihu.com/p/486710656)知乎文章。我将于进一步学习CV后进行更新。


## Positional Encoding
`Positional Encoding`是由Google于2017年提出的，被用于`Transformer`中。简而言之，对于每个位置t，有
$$\vec{P _{t}}=\begin{bmatrix}
 sin(\omega_{1} \cdot t)\\
 cos(\omega_{1} \cdot t)\\
 ...\\
 sin(\omega_{\frac{d}{2} } \cdot t)\\
 cos(\omega_{\frac{d}{2} } \cdot t)\\

\end{bmatrix}_{1\times d}$$