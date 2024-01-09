---
title: Servlet
date: 2022-09-30 16:54:05
tags: Servlet
categories: 实践
excerpt: servlet描述
---
# Cookie
[Cookie](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Cookies#set-cookie_%E5%93%8D%E5%BA%94%E5%A4%B4%E9%83%A8%E5%92%8Ccookie_%E8%AF%B7%E6%B1%82%E5%A4%B4%E9%83%A8)
<!-- more -->
## 定义：
- Cookies 是存储在客户端计算机上的文本文件，并保留了各种跟踪信息。Java Servlet 显然支持 HTTP Cookies。
- Cookie，有时也用其复数形式 Cookies。类型为“小型文本文件”，是某些网站为了辨别用户身份，进行Session跟踪而储存在用户本地终端上的数据（通常经过加密），由用户客户端计算机暂时或永久保存的信息[百度](https://baike.baidu.com/item/cookie/1119#:~:text=Cookie%EF%BC%8C%E6%9C%89%E6%97%B6%E4%B9%9F%E7%94%A8%E5%85%B6%E5%A4%8D%E6%95%B0%E5%BD%A2%E5%BC%8F%20Cookies%20%E3%80%82.%20%E7%B1%BB%E5%9E%8B%E4%B8%BA%E2%80%9C%20%E5%B0%8F%E5%9E%8B%E6%96%87%E6%9C%AC%E6%96%87%E4%BB%B6%20%E2%80%9D%EF%BC%8C%E6%98%AF%E6%9F%90%E4%BA%9B%E7%BD%91%E7%AB%99%E4%B8%BA%E4%BA%86%E8%BE%A8%E5%88%AB%E7%94%A8%E6%88%B7%E8%BA%AB%E4%BB%BD%EF%BC%8C%E8%BF%9B%E8%A1%8C%20Session%20%E8%B7%9F%E8%B8%AA%E8%80%8C%E5%82%A8%E5%AD%98%E5%9C%A8%E7%94%A8%E6%88%B7%E6%9C%AC%E5%9C%B0%E7%BB%88%E7%AB%AF%E4%B8%8A%E7%9A%84%E6%95%B0%E6%8D%AE%EF%BC%88%E9%80%9A%E5%B8%B8%E7%BB%8F%E8%BF%87%E5%8A%A0%E5%AF%86%EF%BC%89%EF%BC%8C%E7%94%B1%E7%94%A8%E6%88%B7,%E4%B8%AD%E6%96%87%E5%90%8D.%20%E5%82%A8%E5%AD%98%E5%9C%A8%E7%94%A8%E6%88%B7%E6%9C%AC%E5%9C%B0%E7%BB%88%E7%AB%AF%E4%B8%8A%E7%9A%84%E6%95%B0%E6%8D%AE.%20%E5%A4%96%E6%96%87%E5%90%8D.%20Cookie.%20%E5%A4%8D%E6%95%B0%E5%BD%A2%E5%BC%8F.%20Cookies.%20%E5%88%AB%20%E5%90%8D.)
- 总结：cookie就是保存浏览器信息，来进行追踪，识别
## 识别三步骤：
-   第一次浏览器访问服务器，set-cookie如果有人为设置cookie就执行人为设置，且发送给客户端，如果没用认为设置就随机生成
-   下次同一浏览器访问同一请求就是不会创建cookie值了
-   存活
    -   在浏览器关闭就失败
    -   设置存活时间，如果时间就，及时关闭了浏览器，cookie依旧在，因为将值不仅仅是存在浏览器中，还存在了硬盘
```
HTTP/1.1 200 OK
Date: Fri, 04 Feb 2000 21:03:38 GMT
Server: Apache/1.3.9 (UNIX) PHP/4.0b3
Set-Cookie: name=xyz; expires=Friday, 04-Feb-07 22:03:38 GMT; 
                 path=/; domain=w3cschool.cn
Connection: close
Content-Type: text/html
```