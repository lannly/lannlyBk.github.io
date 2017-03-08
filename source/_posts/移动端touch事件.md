---
title: 移动端touch事件
date: 2016-10-31 09:52:18
comments: true
categories: 学习笔记
tags: [笔记]
keywords: touch, 移动端, 手势
description: 移动端touch手势~
---

/* 当用户手指放在移动设备在屏幕上滑动会触发的touch事件 */
// 以下支持webkit
1. touchstart——当手指触碰屏幕时候发生。不管当前有多少只手指
2. touchmove——当手指在屏幕上滑动时连续触发。通常我们再滑屏页面，会调用event的preventDefault()可以阻止默认情况的发生：阻止页面滚动
3. touchend——当手指离开屏幕时触发
4. touchcancel——系统停止跟踪触摸时候会触发。例如在触摸过程中突然页面alert()一个提示框，此时会触发该事件，这个事件比较少用

//TouchEvent说明：
1. touches：屏幕上所有手指的信息
2. targetTouches：手指在目标区域的手指信息
3. changedTouches：最近一次触发该事件的手指信息
4. touchend时，touches与targetTouches信息会被删除，changedTouches保存的最后一次的信息，最好用于计算手指信息

//参数信息(changedTouches[0])
clientX、clientY在显示区的坐标
target：当前元素

//事件响应顺序
`ontouchstart  > ontouchmove  > ontouchend > onclick`
  
|     类型     |          触发条件                    |
|--------------|--------------------------------------|
|  touchstart  |    手指触摸动作开始                  |
|  touchmove   |    手指触摸后移动                    |
|  touchcancle |    手指触摸被打断，比如来电提醒，弹窗|
|  tap         |    手指触摸后马上离开                |
|  longtap     |    手指触摸后,超过350ms再离开        |
|  touchend    |    手指触摸动作结束                  |