---
title: js截取字符串
date: 2016-10-31 15:05:42
comments: true
categories: 学习笔记
tags: [笔记]
keywords: Blog, hexo
description: js中字符截取函数有常用的三个slice()、substring()、substr();
---
在js中字符截取函数有常用的三个slice()、substring()、substr()
	`slice(start,[end])` `substring(start,[end])`和 `substr(start,[length]) `

#### slice()
第一个参数代表开始位置,第二个参数代表结束位置的下一个位置,截取出来的字符串的长度为第二个参数与第一个参数之间的差;
若第二个参数值为负数,则将该值加上字符串长度后转为正值;
若第一个参数等于大于第二个参数,则返回空字符串.
```javascript
var str = "0123456789";
alert(str.slice(0))   //返回整个字符串(从第1个字符开始,截取到最后个字符);返回"3456789"
alert(str.slice(3))   //从第4个字符开始,截取到最后个字符; 返回"3456789"
alert(str.slice(3,7))   //从第4个字符开始，到第7个字符  输出"3456"
alert(str.slice(3,-3))   //从第4个字符开始，到第7个字符  输出"3456"
alert(str.slice(5,1)); // 弹出第6个到第8个 返回"空字符串" ps:第一个参数等于大于第二个参数,则返回空字符串.
```
####  substring()
第一个参数代表开始位置,第二个参数代表结束位置的下一个位置;
`若2个参数都为正数时，substring()语法与slice()一致`
若参数值为负数,则将该值转为0;两个参数中,取较小值作为开始位置，截取出来的字符串的长度为较大值与较小值之间的差.
`例如：substring(2,-5)实际上是substring(2,0),负数转换为0,substring总是把较小的数作为起始位置。即输出从下标为1到第二个`
```javascript
	 var str = "0123456789";  //长度为10
	 alert(str.substring(0)); // 弹出全部字符串 输出"0123456789"
	 alert(str.substring(0,2)); // 弹出第一个到第二个  输出"01"
	 alert(str.substring(5,8)); // 弹出第6个到第8个 输出"567"
	 alert(str.substring(5,20)); // 弹出第6个到最后一个 输出"56789",ps:最后一个数大于长度
	 alert(str.substring(5,1)); // 弹出第2个到第5个 输出"1234"   ps:若第一个参数等于大于第二个参数,substring总是把较小的数作为起始位置.
	 alert(str.substring(5,7)); // 弹出第6个到第7个 输出"56"
	 alert(str.substring(5,-3)); // 此例子中等价于 alert(str.substring(5,0));   输出"01234"
```

#### substr()
第一个参数代表开始位置,第二个参数代表截取的长度
PS：字符串都从0开始计起
```javascript
	var str = "0123456789";
	alert(str.substr(0))   //返回整个字符串(从第1个字符开始,截取到最后个字符); 返回"3456789"
	alert(str.substr(3))   //从第4个字符开始,截取到最后个字符;返回"3456789"
	alert(str.substr(3,5))   //从第4个字符开始，输出长度为7个字符。输出"34567"
	alert(str.substr(3,9))   //从第4个字符开始，输出长度为7个字符。输出"3456789"
	alert(str.substr(3,-3))   //从第4个字符开始，到第7个字符输出"3456"
```
---
### 扩展
#### split() 
