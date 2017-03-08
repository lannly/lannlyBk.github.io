---
title: Hexo+Next 添加菜单分类
date: 2016-11-16 13:38:43
comments: true
categories: hexo 
tags: [hexo,菜单]
keywords: hexo,next主题,菜单
description: 下文是笔者记录在[Hexo+Next]添加菜单分类的一个过程;
---

下文是笔者记录在[Hexo+Next]添加菜单分类的一个过程;
> 默认的有：首页，归档，分类，标签，关于, 但是next主题默认只显示了首页 归档和标签。

#### 生成 关于我 (默认已有的分类)
```bash
$ hexo new page "about"
//在 hexo > source 文件夹中会出现一个about文件夹
```
#### 生成 分类 (默认已有的分类) 
```bash
$ hexo new page "categories"
```
步骤：
1. 新建page: $ hexo new page "categories" ，在 hexo > source 文件夹中会出现一个categories文件夹
2. 打开categories文件夹中的index.md页面，在头部添加 -- type: "categories" （为了点击的时候链接生效）
3. 在hexo > theme > next > _config.yml 中修改menu下的categorues,去掉前面井号注释。

#### 生成 作品 (默认没有此分类)
```bash
$ hexo new page "works"
```
步骤：
1. 新建page: $ hexo new page "works" ，在 hexo > source 文件夹中会出现一个categories文件夹
2. 在hexo > theme > next > _config.yml 中menu下添加       --- works: /works  
3. 在hexo > theme > next > _config.yml 中menu_icons下添加 ---   works: book  (ps:2,3步骤如下图)
![添加菜单：作品](/img/works.png)
4. 新添加的菜单需要翻译对应的汉字，打开 hexo　> theme > next > languages > zh-Hans.yml , 在menu下添加--  works: 作品,如下图：
![添加菜单：作品中文翻译](/img/zhhans.png)

That's all~
