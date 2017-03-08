---
title:  css选择器--- nth-child()
date: 2016-11-02 20:23:10
comments: true
categories: 学习笔记
tags: [css]
keywords: css
description: css选择特定的元素,比如选择大于7的 等等~
---
:first-child             第一个
:last-child              最后一个
:nth-of-type(2)          (顺数)第二个
:nth-last-of-type(2)     倒数第二个

:nth-child(2n)                偶数标签，2n也可以是even
:nth-child(2n-1)              奇数标签，2n-1可以是odd
:nth-child(3n+1)              自定义选取标签，3n+1表示“隔二取一”

:nth-child(8)  选中第8个子元素
正方向范围    :nth-child(n+6)        选中从第6个开始的子元素    （大于6的标签 )
负方向范围    :nth-child(-n+9)       选中从第1个到第9个子元素  （小于9的标签 )
前后限制范围  :nth-child(n+4):nth-child(-n+8)  选中第4-8个子元素  （4~8之间的标签）

:nth-child(3n+1):nth-child(even)   间隔选择子元素
使用 :nth-child(3n+1) 我们可以每隔3个选中一个，也就是第 1, 4, 7 和 10 个子元素，但通过使用 :nth-child(even) 我们过滤掉了奇数位子元素，也就是 1 和 7，于是，剩下的子元素只有 4 和 10。

------
`扩展`
jquery 选择元素 eq(0)

$("p:eq(0)")   选择第1个 <p> 元素  等价于：` $("p").eq(0) ` 
:eq()选择器 .eq() jQuery函数
$("tr:gt(2)")  选择前 3 个之后的<tr> 元素：(选择索引值32的元素 index从0开始 )
$("tr:lt(2)")  选择前 2 个 <tr> 元素  (选择索引值<2的元素 index从0开始 )