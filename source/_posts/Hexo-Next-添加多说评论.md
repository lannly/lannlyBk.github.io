---
title: Hexo+Next 多说评论
date: 2016-11-11 13:16:15
comments: true
categories: hexo 
tags: [hexo,多说]
keywords: hexo,next主题,多说,评论
description: Hexo默认使用的评论插件是Disqus,本文章主要是讲解Next主题添加多说。首先进入多说官网注册账号（找了好久也没看到注册页，直接用QQ登录了），登录之后进入“http://duoshuo.com/create-site”创建站点……
---

1. Hexo默认使用的评论插件是Disqus,本文章主要是讲解Next主题添加多说。首先进入[多说官网](http://duoshuo.com/)注册账号（找了好久也没看到注册页，直接用QQ登录了），登录之后进入“http://duoshuo.com/create-site” 创建站点 `ps:该入口有点难找，记录一下`，如下图（我的多说创建过程:新建站点时会创建多说域名：http://lannly.duoshuo.com ,其中lannly为配置文件_config.yml中duoshuo_shortname字段的值）：
![创建站点](/img/duoshuozhandian.png)
2.打开站点配置文件（_config.yml）中新增 duoshuo_shortname 字段，值设置成上一步中的值。
duoshuo_shortname: lannly
3. 修改themes\next\layout\ _partial\archive.swig 模板
	把
	```
{% if page.comments %}
  <div class="comments" id="comments">
    {% if (theme.duoshuo and theme.duoshuo.shortname) or theme.duoshuo_shortname %}
      <div class="ds-thread" data-thread-key="{{ page.path }}" data-title="{{ page.title }}" data-url="{{ page.permalink }}"></div>

    {% elseif theme.facebook_sdk.enable and theme.facebook_comments_plugin.enable %}
      <div class="fb-comments"
           data-href="{{ page.permalink }}"
           data-numposts="{{ theme.facebook_comments_plugin.num_of_posts }}"
           data-width="{{ theme.facebook_comments_plugin.width }}"
           data-colorscheme="{{ theme.facebook_comments_plugin.scheme }}">
      </div>
    {% elseif theme.disqus_shortname %}
      <div id="disqus_thread">
        <noscript>
          Please enable JavaScript to view the
          <a href="//disqus.com/?ref_noscript">comments powered by Disqus.</a>
        </noscript>
      </div>
    {% endif %}
  </div>
{% endif %}
	```
	改成
	```
	{% if page.comments %}
  <div class="comments" id="comments">
    {% if (theme.duoshuo and theme.duoshuo.shortname) or theme.duoshuo_shortname %}
      <!--<div class="ds-thread" data-thread-key="请将此处替换成文章在你的站点中的ID" data-title="请替换成文章的标题" data-url="请替换成文章的网址"></div>-->
      <!-- 多说评论框 start -->
      <div class="ds-thread" data-thread-key="{{ page.path }}" data-title="{{ page.title }}" data-url="{{ page.permalink }}"></div>
      <!-- 多说评论框 end -->
      <!-- 多说公共JS代码 start (一个网页只需插入一次) -->
      <script type="text/javascript">
      var duoshuoQuery = {short_name:"lannly"}; <!--这里的lannly 改成你自己站点的short_name-->
        (function() {
          var ds = document.createElement('script');
          ds.type = 'text/javascript';ds.async = true;
          ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
          ds.charset = 'UTF-8';
          (document.getElementsByTagName('head')[0] 
           || document.getElementsByTagName('body')[0]).appendChild(ds);
        })();
        </script>
      <!-- 多说公共JS代码 end -->

    {% elseif theme.facebook_sdk.enable and theme.facebook_comments_plugin.enable %}
      <div class="fb-comments"
           data-href="{{ page.permalink }}"
           data-numposts="{{ theme.facebook_comments_plugin.num_of_posts }}"
           data-width="{{ theme.facebook_comments_plugin.width }}"
           data-colorscheme="{{ theme.facebook_comments_plugin.scheme }}">
      </div>
    {% elseif theme.disqus_shortname %}
      <div id="disqus_thread">
        <noscript>
          Please enable JavaScript to view the
          <a href="//disqus.com/?ref_noscript">comments powered by Disqus.</a>
        </noscript>
      </div>
    {% endif %}
  </div>
{% endif %}
	```
`上面两段的不同即为下图中的红色区域，替换即可`
![创建站点](/img/duoshuo.png)

*****
### 如何关闭新建页面的评论功能？
当集成了评论系统，如 多说 或者 Disqus，所有新建的页面都将自动开启评论。若你不需要评论，比如标签页，请在页面的 Front-matter 里添加 comments 字段，并将值设置为 false。如下所示：
```bash
---
title: All tags
date: 2016-11-11 17:05:24
type: "tags"
comments: false
---
```
