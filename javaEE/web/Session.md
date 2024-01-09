---
title: Session
date: 2022-10-08 09:40:39
tags: web
---
# 概念
-  Session：在计算机中，尤其是在网络应用中，称为“会话控制”。Session对象存储特定用户会话所需的属性及配置信息。这样，当用户在应用程序的Web页之间跳转时，存储在Session对象中的变量将不会丢失，而是在整个用户会话中一直存在下去。
<!-- more -->
# 存储
Session存储在服务器中，Cookie是保证在客户机上，详见看Cookie


# Session和Cookie的关系
Session因为保存在服务器，Cookie保存在客户机上，Cookie相当于是钥匙，去访问服务器上对应的Session域，（现在能解释为什么第一次浏览器第一次访问服务器，会创建Set-Cookie）

如果服务器出现问题 如重启，对应的Session也会失效，


# 参考
- [Session和cookie实现](https://juejin.cn/post/6942852054847062053)