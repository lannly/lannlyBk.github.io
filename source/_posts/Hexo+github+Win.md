---
title: Hexo+github+Windows
layout: post
date: 2016-10-08 16:13:02
comments: true
categories: hexo
tags: [hexo]
keywords: Blog, hexo
description: windows环境下搭建hexo+github博客
---
## 安装环境
* 安装node.js，去官网下载安装即可，我安装的是最新稳定版,一路next安装到C盘。
	```bash
	$ npm install cnpm -g
	```
	国内的小伙伴可能被墙了，可以使用淘宝的npm镜像
	```bash
	$ npm install cnpm -g --registry=https://registry.npm.taobao.org
	```
	或者直接通过添加 npm 参数 alias 一个新命令:
	```bash
	alias cnpm="npm --registry=https://registry.npm.taobao.org \
	--cache=$HOME/.npm/.cache/cnpm \
	--disturl=https://npm.taobao.org/dist \
	--userconfig=$HOME/.cnpmrc"
	```
	检测nodejs和npm,cnpm是否安装成功
	```bash
	node -v
	npm -v
	cnpm -v
	```

* 安装hexo `如果是Windows平台，则下载[msysgit](https://git-for-windows.github.io/)安装建议勾选Git Bash Here，方便以后的操作，然后一路next即可。`
```
sudo npm install -g hexo
```

* 创建hexo目录并初始化
```bash
$ mkdir hexo  //创建目录hexo
$ cd hexo     //打开目录hexo
$ hexo init   //初始化
```
* 然后就可以生成网站，启动服务了：
```bash
$ hexo clean      //清除
$ hexo generate   //生成目录
$ hexo server     //开启本地服务 http://localhost:4000
```
* hexo文件夹,先来看一下hexo文件夹下的内容：
```
hexo/
  |- node_modules/  # hexo需要的模块，不需要上传GitHub
  |- themes/        # 主题文件，需要上传GitHub的dev分支
  |- sources/       # 博文md文件，需要上传GitHub的dev分支
  |- public/        # 生成的静态页面，由hexo deploy自动上传到gh-page分支
  |- package.json   # 记录hexo需要的包信息，不需要上传GitHub
  |- _config.yml    # 全局配置文件，需要上传GitHub的dev分支
  |- .gitignore     # hexo生成默认的.gitignore，它已经配置好了不需要上传的hexo文件
```
***
## 主题的配置和优化(以next主题为例)
* 安装主题
``` bash
$ hexo clean
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```
* 启用主题
	`修改站点配置文件_config.yml， 找到 theme 字段，并将其值更改为 next `
* 更新主题
```bash 
$ cd themes/next
$ git pull
$ hexo g              # 生成
$ hexo s              # 启动本地web服务器
```
---
## 每次写文章的步骤：

``` bash
$ hexo new(n) "文章标题"    //写文章
$ hexo generate(g)    //把文章生成页面
$ hexo server(s)    //启动本地服务调试
$ hexo deploy(d)    //部署到github 可与hexo g合并为 hexo d -g
```
ps:`hexo d`之前要安装一个扩展
```bash
 $ npm install hexo-deployer-git --save
```
***
### clone github repo
```bash
$ cd d:/hexo/blog
$ git clone https://github.com/lannly/lannly.github.io.git .deploy/lannly.github.io
```
### 创建一个deploy脚本文件
```bash
hexo generate
cp -R public/* .deploy/jiji262.github.io
cd .deploy/jiji262.github.io
git add .
git commit -m “update”
git push origin master
```
`ps:简单解释一下，hexo generate生成public文件夹下的新内容，然后将其拷贝至lannly.github.io的git目录下，然后使用git commit命令提交代码到lannly.github.io这个repo的master branch上`


***
## 绑定独立域名
`在你的域名注册提供商那里配置DNS解析，获取GitHub的IP地址点击，进入source目录下，添加CNAME文件`
```bash
$ cd source/
$ touch CNAME
$ vim CNAME # 输入你的域名
$ git add CNAME
$ git commit -m "add CNAME"
```

***
## 文章中插入网易云音乐
```html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="http://music.163.com/outchain/player?type=2&id=28947001&auto=1&height=66"></iframe>
<!-- 如果只是加入单曲，只需要搜索歌曲，点开歌曲名，点击生成外链播放器，复制html代码（可以选择是否自动播放），将html代码无需任何修改放入markdown文章里就OK了。 -->
<!-- 如果想要加入歌单，就需要自己创建歌单，然后分享歌单，找到自己的分享动态，点进去可以看到有“生成外链播放器”这些字眼，其余操作就和上面一样了。不过，你的歌单有变化的话，这个外链的歌曲同样跟着变，这一点挺棒的。 -->
```
------
## hexo填坑：
1.安装hexo关于git管理组件：hexo-delopyer-git
```bash

$ npm install hexo-deplyer-git --save
```
2.最近使用next主题站点打不开首页，出现白屏，报错信息如下图：
	![mahua](/img/vendorsError.png)
	解决办法：
	1.打开主题目录 hexo\themes\next\source\vendors ,将vendors文件夹名称改为 lib 
	![gg](http://ogtg6fa5t.bkt.clouddn.com/lib1.png)
	2.打开主题配置文件 hexo\themes\next\ _config.yml ,找到 vendors,修改为： _internal: lib 
	![gg](http://ogtg6fa5t.bkt.clouddn.com/lib2.png)
	说明：![gg](/img/vendors.png)
	