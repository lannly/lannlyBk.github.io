---
title: about
date: 2016-11-10 18:01:27
comments: false
---
> 关于我,你了解甚麼？

``~未完，待续``

<script>
	(function(IM,STATE,SINCE){
    var now = new Date();                        
    var profile = {
        '姓名':'lannYu',
        '年龄':(now.getFullYear()-SINCE),
        '性别':'女',
        '标签':['Front-end Developer','宅'],
        '喜欢':['移动互联网','前端','交互设计','深度学习','电影','爬山','美食...'],
        '家乡':'武汉'
    };
    var HH = function(data){
        this.profile = profile;
        var that = this;
        this.Dream = '世界和平…';
        this.Words = '欲戴皇冠，必承其重';
        this.profile.昵称 = IM;
        this.profile.状态 = STATE;
        this.OwnDream = function(){
            return that.profile.梦想 = that.Dream;
        };
        this.MostLikeWords = function(){
            return that.profile.座右铭 = that.Words;
        };
        this.SelfIntro = function(){
            for(tag in that.profile){
                if('object' == typeof(that.profile[tag])){
                    that.profile[tag] = that.profile[tag].join(', ');
                }
                console.log(tag+':',that.profile[tag]);
            }
        };
    };
    var me = new HH( );
        me.OwnDream();
        me.MostLikeWords();
        me.SelfIntro();
})('lann','努力赚钱，努力花钱......','1990')
</script>