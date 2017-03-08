---
title: Hexo+github+Mac
layout: post
date: 2016-10-08 18:17:02
comments: true
categories: hexo
tags: [hexo]
keywords: Blog, hexo
description: Mac环境下搭建hexo+github博客
---

### 安装Hexo
`sudo npm install-g hexo `  (ps: sudo是Linux系统管理指令 -g:全局安装)

### 创建hexo目录并初始化
```bash
$ mkdir hexo  //创建目录hexo
$ cd hexo     //打开目录hexo
$ hexo init   //初始化
$ npm install //安装依赖
```
### 然后就可以生成网站，启动服务了：
```bash
$ hexo clean      //清除
$ hexo generate   //生成目录
$ hexo server     //开启本地服务 http://localhost:4000
```



### 填坑
$ hexo d 报错
ERROR Deployer not found: Git
解决方法如下：
> npm install hexo-deployer-git –save
