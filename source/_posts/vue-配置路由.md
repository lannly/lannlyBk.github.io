---
title: vue-配置路由
date: 2017-01-19 09:45:12
comments: true
categories: vue
tags: [vue,vue-router]
keywords: vue,vue-router
description: 下文主要vue2.0 + vue-router的一些配置，比较适合初学者~
---
随着vue2.0的出现，vue1.0中的路由配置router.map被舍弃了，下文主要是介绍一下vue2.0的路由配置方法。

#### 首先在main.js文件中引入相关模块以及组件
```
import Vue from 'vue'
import App from './App'
import router from './router'    //这里引入的是router目录，会默认识别里面的index.js文件（不能是其他名字）

// 引入并使用vue-resource网络请求模块
import VueResource from 'vue-resource'
Vue.use(VueResource)

new Vue({        //实例化vue对象配置选项路由及渲染App组件
  el: '#app',    //这里绑定的是index.html中的id为app的div元素
  router,
  render: h => h(App)

})

```

#### App.vue文件
```
<template>
  <div id="app">
    <ul>
      <li><router-link to="/home">Home</router-link></li>
      <li><router-link to="/about">About</router-link></li>
    </ul>
   <router-view></router-view>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {
    // Hello
  }
}
</script>

<style>
</style>
```

#### 在router/index.js文件中创建路由并配置路由映射
```
// 这里面负责写路由映射，便于管理


// 引入路由模块并使用它
import Vue from 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)



// 创建路由实例并配置路由映射  
// path:'*',redirect:'/home'  重定向到path是/home的映射
const router = new VueRouter({
  routes:[{
      path: '/home', component: require('../components/Home.vue')
  },{
      path: '/about', component: require('../components/About.vue')
  },{
      path:'*',redirect:'/home'
  }]
})

// 输出router
export default router;
```

#### Home.vue  地址：(src/components/Home.vue)
```
<template>
  <div class="home">
    <h1>{{ msg }}</h1>
    <ul>
      <li v-for="article in articles">
        
          <div class="m-img inl-block"><img v-bind:src="article.images.small"/></div>
       <div class="m-content inl-block">
          <div>{{article.title}}</div>
        <div>年份：{{article.year}}</div>
         <div>类型：{{article.subtype}}</div>
       </div>
      </li>
    </ul>
  </div>
</template>

<script>

// mounted 钩子函数  这里去请求豆瓣数据

export default {
  name: 'home',
  data () {
    return {
      msg: '电影列表',
      articles:[]
    }
  },
  created:function(){  //这里mounted和created生命周期函数区别
     this.$http.jsonp('https://api.douban.com/v2/movie/top250?count=10', {}, {
        headers: {

        },
        emulateJSON: true
    }).then(function(response) {
      // 这里是处理正确的回调
        console.log(response);
        this.articles = response.data.subjects
        // this.articles = response.data["subjects"] 也可以

    }, function(response) {
        // 这里是处理错误的回调
        console.log(response)
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul{
  list-style: none;
  margin: 0;
  padding: 0;
}
ul li{
border-bottom: 1px solid #999;
padding: 10px 0;
}

.inl-block{
display: inline-block;
}

.m-img{
  
}
.m-content{
margin-left: 20px;
}
</style>
```