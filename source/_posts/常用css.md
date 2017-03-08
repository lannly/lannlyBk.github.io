---
title: 常用css
date: 2016-11-02 10:41:52
comments: true
categories: 学习笔记
tags: [css]
keywords: css
description: 以下是常用的代码收集，没有任何技术含量，只是填坑的积累
---

#### 文字只显示一行，超出部分显示省略号：
```css
.nowrap {
	width:100%; //加个宽度 超出显示省略号
	text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
	
}
```
#### 多行文字截断：
```css
.ui-nowrap-multi {
	display: -webkit-box;
	overflow: hidden;
	text-overflow: ellipsis;
	-webkit-box-orient: vertical;
	-webkit-line-clamp: 2;//默认两行
}
```

#### 文本垂直居中
```css
.txt{
	display : -webkit-box ;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    -webkit-justify-content : center ;
    justify-content: center;
    -webkit-box-align: center;
    -ms-flex-align: center;
    -webkit-align-items: center;
    align-items: center;
    }
```
#### flex布局
```css
.parent{
	display:-webkit-box;
	display:-moz-box;
	display:-ms-flexbox;
	display:-webkit-flex;
	display:flex;
}
.child{
	-webkit-box-flex:1;
	-moz-box-flex:1;
	-webkit-flex:1;
	-ms-flex:1;
	flex:1;
}
```

#### 垂直水平翻转
```css

/*水平翻转*/
.flipx {
    -moz-transform:scaleX(-1);
    -webkit-transform:scaleX(-1);
    -o-transform:scaleX(-1);
    transform:scaleX(-1);
    filter:FlipH;     /*IE*/
}

/*垂直翻转*/
.flipy {
    -moz-transform:scaleY(-1);
    -webkit-transform:scaleY(-1);
    -o-transform:scaleY(-1);
    transform:scaleY(-1);
    filter:FlipV;    /*IE*/
}

/*或者 (ps:基于webkit核心的浏览器)*/

.flipx { transform: rotateY(180deg); } /*水平翻转*/
.flipy { transform: rotateX(180deg); } /*垂直翻转*/
```

#### css 滤镜 暗化效果：
首先新建一个blue.svg文件
```html
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1"
     xmlns="http://www.w3.org/2000/svg"
     xmlns:xlink="http://www.w3.org/1999/xlink"
     xmlns:ev="http://www.w3.org/2001/xml-events"   
     baseProfile="full"> 
    <defs>
        <filter id="blur">
            <feGaussianBlur stdDeviation="10" />
        </filter>
    </defs>
</svg>
```
css样式：
```css
.filter-brightness{
    filter: url(blur.svg#blur); /* FireFox, Chrome, Opera */    
    -webkit-filter: blur(10px) brightness(.3); /* Chrome, Opera */
    -moz-filter: blur(10px) brightness(.3);
    -ms-filter: blur(10px) brightness(.3);   
    filter: blur(10px) brightness(.3); 
}

```

#### 页面变灰
```css
html{
	filter: grayscale(100%);
	-webkit-filter: grayscale(100%);
	-moz-filter: grayscale(100%);
	-ms-filter: grayscale(100%);
	-o-filter: grayscale(100%);
	filter: url("data:image/svg+xml;utf8,<svg xmlns=\'http://www.w3.org/2000/svg\'><filter id=\'grayscale\'><feColorMatrix type=\'matrix\' values=\'0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0 0 0 1 0\'/></filter></svg>#grayscale");
	filter:progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
	-webkit-filter: grayscale(1);
}
```
#### 渐变遮挡（透明层遮挡）
```css
.overlay {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	transition: all .2s ease 0s;
	background-image: linear-gradient(180deg,rgba(0,0,0,.01) 30%,rgba(0,0,0,.95) 100%);
}
```
#### 画三角形
```css
/*把上、左、右三条边隐藏掉（颜色设为 transparent）*/
#demo {
	width: 0;
	height: 0;
	border-width: 20px;
	border-style: solid;
	border-color: transparent transparent red transparent;
}
```
#### 多张背景图
```css
.content1 .main .indiana .item {
	position: relative;
	width: 100%;
	background-image: url(../img/index1/border.png),url(../img/index1/border.png);
	background-repeat: no-repeat, no-repeat;
	background-size: 100% 100%;
	background-position: left 0, right 0;
}
```

