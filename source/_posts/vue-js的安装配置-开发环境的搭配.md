---
title:  vue.js的安装配置(开发环境的搭配)
date: 2017-01-06 10:17:15
comments: true
categories: vue
tags: [vue]
keywords: vue
description: Vue.js作为目前最热门最具前景的前端框架之一，其提供了一种帮助我们快速构建并开发前端项目的新的思维模式。本文旨在帮助大家认识Vue.js，了解Vue.js的开发流程，并进一步理解如何通过Vue.js来构建一个中大型的前端项目，同时做好相应的部署与优化工作。
---

#### 技术栈
前言：为了我们快速使用Vue.js构建前端项目可能会用到：
`vue-cli`：Vue.js脚手架，用于自动生成Vue.js项目。
`vue-router`：Vue.js提供前端路由工具，实现页面路由控制，局部刷新和按需加载等。
`vuex`：Vue.js提供的状态管理工具，用于统一管理和存储项目中的各种数据。
`ES6`：Vue.js普遍使用ES6编写代码。
`NPM`：Node.js包管理这个就不用多说了。
`Webpack`：最近很火的一款强大文件打包工具。
`Babel`：装X必备工具，将ES6代码转化成浏览器兼容的ES5代码插件。
****

在使用vue-cli之前我们需要安装node.js，利用其提供的npm命令来安装vue-cli。安装node.js只需去其官网下载软件并安装即可，地址为：[https://nodejs.org/en/](https://nodejs.org/en/),鉴于国内要翻墙，也可以直接用淘宝镜像,推荐网址：[https://npm.taobao.org/](https://npm.taobao.org/)。
`ps:如果使用淘宝镜像安装就输入命令行 $  cnpm install -g vue-cli进行安装，如果没有安装淘宝镜像依旧用$ npm install -g vue-cli安装：`
#### 在node的npm下输入以下命令行：

```
(npm)cnpm install -g vue-cli                       //全局安装vue-cli
(npm)cnpm install -g webpack                       //全局安装webpack
(npm)cnpm install -g webpack-dev-server            //安装webpack的本地webserver
```

`安装完成后，vue-cli脚手架其实就已经把vue也装掉了，所以只需输入vue -V 和 webpack -v 等等就可以查看安装成功与否`
#### 新建一个vue项目：
```
vue init webpack my-project: 利用vue-cli在目录地址生成一个基于webpack的名为’my-project‘的Vue项目文件及目录
cd my-project：打开刚刚创建的文件夹 (该文件夹默认在c盘>用户>你的用户名下面)
npm intall：安装项目所依赖的包文件,安装成功后在你的项目文件夹中多了一个额“node_modules”文件夹
npm run dev：利用本地node服务器在浏览器中打开并浏览项目页面
```
npm run dev之后你就会在浏览器中看到你的页面啦，到这里vue项目开发环境的搭建就基本完成了~

***

* 打包项目
```
npm run build
```
* 单元测试
```
npm run unit
```
* e2e测试
```
npm run e2e
```
* 单独安装一个包
```
npm install vue-router --save-dev
```

# 开发工具
## Vue.js devtools
* chrome Vue开发插件——
[安装地址](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd?hl=zh-CN)

# 学习资料
* [vuejs文档](http://cn.vuejs.org/)
* [vuex文档](http://vuex.vuejs.org/) ——（状态管理插件）
* [vue-router文档](http://router.vuejs.org/) ——（路由管理插件）
* [vue-resource文档](https://github.com/vuejs/vue-resource/tree/master/docs) ——（ajax插件）
* [vue-validator文档](http://vuejs.github.io/vue-validator/) ——（表单验证插件）
* [vuejs2.0文档-English](http://rc.vuejs.org/)
* [vuejs2.0文档-中文版](http://vuefe.cn/)
* [vue-router2.0文档](https://github.com/vuejs/vue-router/tree/next/docs/en)
* [ECMAScript 6入门](http://es6.ruanyifeng.com/)

# 开源项目
* [饿了么前端开源项目（很多项目用到vuejs）](https://github.com/ElemeFE)
* [蘑菇街移动端Vue-SPA](https://github.com/andylei18/vue-shopping)
* [Element（饿了么基于vue2.0的开源组件库）](http://element.eleme.io/)
* [HackerNews（vue2.0官方范例）](https://vue-hn.now.sh/top)