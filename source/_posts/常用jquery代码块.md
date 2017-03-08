---
title: 常用jQuery代码块
date: 2016-12-08 09:36:01
comments: true
categories: jQuery 
tags: [jQuery,代码块]
keywords: jQuery,jQuery
description: 下文是笔者记录一些常用的jquery代码块，日常搬砖积累~;
---

### 动态加载css
```js 
function loadCss(url){
	var link = document.createElement("link");
	link.type = "text/css";
	link.rel = "stylesheet";
	link.href = url ;
	var head = document.getElemensByTagName("head")[0];
	head.appendChild(link);
}
loadCss("css/index.js");  //需要时候调用 ，比如加载css文件夹下面的index.js

```
### 动态加载js
```js 
function loadScript(url){
	var script = document.createElement("script");
	script.type = "text/javascript";
	script.src = url ;
	document.body.appendChild(script);
}
loadScript("js/juqery.js");  //需要时候调用 ，比如加载js文件夹下面的juqery.js

```
### 特殊操作下，项目中同时引入这两个文件时，往往会有些冲突，应该加一句代码避免冲突
```html
<script src="js/jquery-2.1.4.js"></script>
<script>jQuery.noConflict()</script>
<script src="js/zepto.min.js"></script>

```



### jQuery获取Select选择的Text和Value:
```js
$("#select_id").change(function(){//code...});  //为Select添加事件，当选择其中一项时触发
var checkText=$("#select_id").find("option:selected").text();  //获取Select选择的Text
var checkValue=$("#select_id").val();   //获取Select选择的Value
var checkIndex=$("#select_id ").get(0).selectedIndex;   //获取Select选择的索引值 
var maxIndex=$("#select_id option:last").attr("index");   //获取Select最大的索引值
```
### jQuery设置Select选择的Text和Value:
```js
$("#select_id ").get(0).selectedIndex=1;   //设置Select索引值为1的项选中
$("#select_id ").val(4);    //设置Select的Value值为4的项选中 
$("#select_id option[text='jQuery']").attr("selected", true);  //设置Select的Text值为jQuery的项选中 
```

### jQuery添加/删除Select的Option项：
```js
$("#select_id").html("<option value='Value'>Text</option>");   //为Select设置Option(下拉项) 
$("#select_id").append("<option value='Value'>Text</option>"); //为Select追加一个Option(下拉项)
$("#select_id").prepend("<option value='0'>请选择</option>");  //为Select插入一个Option(第一个位置) 
$("#select_id option:last").remove();         //删除Select中索引值最大Option(最后一个)
$("#select_id option[index='0']").remove();   //删除Select中索引值为0的Option(第一个)
$("#select_id option[value='3']").remove();   //删除Select中Value='3'的Option
$("#select_id option[text='4']").remove();    //删除Select中Text='4'的Option

```
### jQuery清空Select:
```js
$("#ddlRegType ").empty();
```

### 图片预加载
```js 
 jQuery.preloadImages = function () {
        for (var i = 0; i < arguments.length; i++) {
            $("<img />").attr('src', arguments[i]);
        }
};

$.preloadImages('image1.gif', '/path/to/image2.png', 'some/image3.jpg'); //用法 存储图片地址

```