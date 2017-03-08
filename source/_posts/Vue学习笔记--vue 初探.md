---
title:  Vue学习笔记--vue 初探
date: 2016-12-22 10:55:45
comments: true
categories: vue
tags: [vue]
keywords: vue
description: 刚接触vue 菜鸟一枚,学习过程中的一些简单实例,加强记忆,随时更新补充~
---



> vue.js重要的组件:

`el`:绑定的对象 ,  `data`:数据,   `method`：方法 ,  `watch`：监听.

控制模块隐藏：v-if、v-show
渲染循环列表：v-for
事件绑定：v-on（其中v-on:click和@click是一样的事件绑定）
属性绑定：v-bind，这个一般绑定的是class属性，所以v-bind会省略
双向绑定 : v-model

vue 周边工具：
vue-loader：与 Webpack 结合进行组件化开发
vueify：与 Gulp 结合进行组件化开发
vue-router：路由
vue-validator：表单验证库
vue-resource：网络请求库
vue-component-complier：与其他预编译器结合
vue-touch：事件模拟
meteor-vue：meteor 与 vue 结合开发
vue-syntax-hightlight：sublime text 的 vue 文件的高亮插件
vue-typeahead：搜索输入提前查询补全
vue-i18n：i18n
vue-devtools：配合 chrome 的开发插件，调试时可用





### 数据绑定
 `三种形式：{ {} }、v-text、v-html效果上没有多大的区别。`
```html
//html
<div id="app1">
	<h3>{{ message }}</h3>
	<div v-text="appText"></div>
	<div v-html="appHtml"></div>
</div>

```
```js
//js
new Vue({
	el:"#app1",
	data:{
	message:"hello vue.js",
	app2Text:"这是appText",
	app2Text:"<strong>这是appText</strong>"
	}
})
```



### 双向绑定 : v-model
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>vue-demos</title>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.3/vue.js"></script>
    </head>
    <body>
        <!-- v-model: 可以直接将表单输入的某个值跟Vue实例的属性绑定-->
        <div id="app">
            <p>{{message}}</p>
            <input v-model="message"></input>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    message: 'Hello Vue.js'
                }
            });
        </script>
    </body>
</html>
```


### v-on绑定多个方法
```js
<input type="text" :value="name" @input="onInput" @focus="onFocus" @blur="onBlur"  v-on:keyup.enter="submit" />
```

### 一个综合实例：
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>vue learn</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.3/vue.js"></script>
</head>
<body>  
<h3>下面是可以添加删除的</h3>
<div id="div1">
<input type="text" @focus="onFocus" @blur="onBlur" v-model="newTodo"  v-on:keyup.enter = "addNewList">
<ul>
  <li v-for="item in items">
    <span :style="spanCss">{{item.text}}</span>
    <span @click="removeList(index)">删除</span>
  </li>
</ul>
</div>
<script>
var app1= new Vue({
  el:"#div1",
  data:{
    newTodo:"输入要添加的回车",
    items:[
      {text:"html5"},
      {text:"css3"}
    ],
    spanCss:{
      display:"inline-block",
      minWidth:"200px",
      color:"red",
      fontSize:"20px",
      backgroundColor:"#ddd",
      marginBottom:"10px"
    }
  },
  methods:{
    onFocus:function(){
      this.newTodo = "";
    },
    onBlur:function(){
      this.newTodo = "输入要添加的回车";
    },
    addNewList:function(){
      var txt =this.newTodo.trim();
      if(txt){
        this.items.push({text:txt});
        this.newTodo ="";
      }
    },
    removeList:function(index){
      this.items.splice(index,1)
    }
     
  }
})
</script>
</body>
</html>
```