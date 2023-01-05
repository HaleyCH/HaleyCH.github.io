title: CSS暗色主题适配、移动端主题适配
author: HaleyCH
tags:
  - css
  - '@media'
cover_image: 'http://i.hluvmiku.tech/f/63b68f1416c02a984b952c2d/'
categories:
  - 前端
abbrlink: ed83e127
date: 2023-01-04 14:16:00
---
省流：`@media (prefers-color-scheme: dark)`、`@media screen and (min-width：)`或 `@media screen and(orientation: portrait)`。

# 前言

在学习Vue3时，参考了下里面默认的 `main.css` 感觉很不错，故打算拿出来讲讲。

# 暗色主题适配

暗色主题适配主要由 `@media (prefers-color-scheme: dark)` 实现。

## 何为@media?
>@media CSS @ 规则可用于基于一个或多个媒体查询的结果来应用样式表的一部分。使用它，你可以指定一个媒体查询和一个 CSS 块，当且仅当该媒体查询与正在使用其内容的设备匹配时，该 CSS 块才能应用于该文档。

`@media` 是一个CSS `@规则` 。如果满足 `@media` 的条件则条件规则组里的规则生效。

__示例：__
```css
/* 当屏幕最小尺寸大于等于900px时触发 */
@media screen and (min-width: 900px) {
  article {
    padding: 1rem 3rem;
  }
}
```

[参考资料](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media)

## 实现暗色主题适配

思路：先定义一系列配色，再使用 `@media (prefers-color-scheme: dark)` 选择合适的颜色。

1. 定义颜色(以我的主页为例,省略部分代码)：
```css
/* color palette by HaleyCH*/
:root {
  --hch-c-black: hsl(196, 100%, 4%);  // 定义主题中的黑色
  --hch-c-white: hsl(195, 80%, 98%);  // 定义主题中的白色

  --hch-c-text-light:hsl(196, 100%, 4%);  // 定义亮色调中文字颜色
  --hch-c-text-dark:hsl(195, 80%, 98%);  // 定义暗色调中文字颜色
}
```

2. 定义默认颜色（默认亮色主题）：
```css
:root{
  --color-background: var(--hch-c-white);  // 亮色主题背景颜色
  --color-text: var(--hch-c-text-light);  // 亮色主题文字颜色
}
```

3. 定义暗色主题（根据系统主题切换）：
```css
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: var(--hch-c-black);  // 暗色主题背景颜色
    --color-text: var(--hch-c-text-dark);  // 暗色主题文字颜色
  }
}
```

# 移动端适配

一般采用`@media screen and (min-width：)`或 `@media screen and(orientation: portrait)`实现。在vue3提供的默认`main.css`中，采用了第一种。

由于思路和[实现暗色主题适配](#实现暗色主题适配)很像，仅提供原理和思路。

## 原理

- `@media screen and (min-width：$xxx)` ： 当屏幕最小宽度大于等于xxx时触发。
- `@media screen and(orientation: portrait)` ： 当 `viewport` 纵向时触发。

其中 `orientation` 的关键字值为以下二者之一：
 
 `portrait`
   viewport 处于纵向，即高度大于等于宽度。
 
 `landscape`
   viewport 处于横向，即宽度大于高度。
   
 ## 思路
 先写PC端的css，再在 `@media` 中写移动端适配。
 
# 总结
`@media` 是css中十分重要的一个 `@规则` ，需要重点掌握。