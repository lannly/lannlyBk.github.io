---
title: markdown语法学习
layout: post
date: 2016-10-08 11:31:57
comments: true
categories: 学习笔记
tags: [markdown]
keywords: markdown, Blog, hexo
description: 刚开始用markdown写博客，对于其语法还不是很熟悉,记录一下,当作学习~
---

#### 标题
* `# 一级标题`
* `## 二级标题`
* `### 三级标题`
***
#### 列表
1. 无序列表: `在文字前加上 - 或 * 即可变为无序列表`
2. 有序列表: `在文字前加上1. 2. 3.即可变为有序列表. ps:符号要和文字之间加上一个字符的空格`
***	
#### 引用
>只需要在文本前加入 > 这种尖括号（大于号）即可 

***
#### 图片与连接
* 图片为：`![Alt text](/path/to/img.jpg "Optional title")`
	1. Alt text 为如果图片无法显示时显示的文字.
	2. /path/to/img.jpg 为图片所在路径 `路径可以使用绝对路径也可以使用相对路径，建议使用相对路径`
	3. Optional title 显示标题。显示效果为在你将鼠标放到图片上后，会显示一个小框提示，提示的内容就是 Optional title 里的内容。
* 链接为：`[]()`
***
#### 粗体与斜体
* `用两个 * 包含一段文本就是粗体的语法`
* `用一个 * 包含一段文本就是斜体的语法`
***
#### 代码框
* 行内代码 用两个 `包含 
***
#### 分割线
`分割线的语法只需要三个 * 号`
***
#### 表格(`tips:原生markdown不支持这样的表格，扩展的markdown才支持`)
```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

