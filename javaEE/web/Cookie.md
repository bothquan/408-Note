---
title: Cookie
date: 2022-10-08 09:25:26
tags: web
---
# 概念
- Cookie，有时也用其复数形式 Cookies。类型为“小型文本文件”，是某些网站为了辨别用户身份，进行Session跟踪而储存在用户本地终端上的数据（通常经过加密），由用户客户端计算机暂时或永久保存的信息[百度][百度](https://baike.baidu.com/item/cookie/1119#:~:text=Cookie%EF%BC%8C%E6%9C%89%E6%97%B6%E4%B9%9F%E7%94%A8%E5%85%B6%E5%A4%8D%E6%95%B0%E5%BD%A2%E5%BC%8F%20Cookies%20%E3%80%82.%20%E7%B1%BB%E5%9E%8B%E4%B8%BA%E2%80%9C%20%E5%B0%8F%E5%9E%8B%E6%96%87%E6%9C%AC%E6%96%87%E4%BB%B6%20%E2%80%9D%EF%BC%8C%E6%98%AF%E6%9F%90%E4%BA%9B%E7%BD%91%E7%AB%99%E4%B8%BA%E4%BA%86%E8%BE%A8%E5%88%AB%E7%94%A8%E6%88%B7%E8%BA%AB%E4%BB%BD%EF%BC%8C%E8%BF%9B%E8%A1%8C%20Session%20%E8%B7%9F%E8%B8%AA%E8%80%8C%E5%82%A8%E5%AD%98%E5%9C%A8%E7%94%A8%E6%88%B7%E6%9C%AC%E5%9C%B0%E7%BB%88%E7%AB%AF%E4%B8%8A%E7%9A%84%E6%95%B0%E6%8D%AE%EF%BC%88%E9%80%9A%E5%B8%B8%E7%BB%8F%E8%BF%87%E5%8A%A0%E5%AF%86%EF%BC%89%EF%BC%8C%E7%94%B1%E7%94%A8%E6%88%B7,%E4%B8%AD%E6%96%87%E5%90%8D.%20%E5%82%A8%E5%AD%98%E5%9C%A8%E7%94%A8%E6%88%B7%E6%9C%AC%E5%9C%B0%E7%BB%88%E7%AB%AF%E4%B8%8A%E7%9A%84%E6%95%B0%E6%8D%AE.%20%E5%A4%96%E6%96%87%E5%90%8D.%20Cookie.%20%E5%A4%8D%E6%95%B0%E5%BD%A2%E5%BC%8F.%20Cookies.%20%E5%88%AB%20%E5%90%8D.)
<!-- more -->
- 服务器可能为每个访问者产生cookie，cookie分为内存cookie和硬盘cookie
  - 内存cookie为关闭浏览器就删除，存在时间短(其决定性因数是Expire属性，或者MAX-age)
  - 硬盘cookie删除需要用户手动删除，当然硬盘出现问题不讨论
# cookie组成
- Cookie是一段不超过4KB的小型文本数据，由一个名称（Name）、一个值（Value）和其它几个用于控制Cookie有效期、安全性、使用范围的可选属性组成。其中   ：
  -   (1)Name/Value：设置Cookie的名称及相对应的值，对于认证Cookie，Value值包括Web服务器所提供的访问令牌   。
  -   (2)Expires属性：设置Cookie的生存期。有两种存储类型的Cookie：会话性与持久性。Expires属性缺省时，为会话性Cookie，仅保存在客户端内存中，并在用户关闭浏览器时失效；持久性Cookie会保存在用户的硬盘中，直至生存期到或用户直接在网页中单击“注销”等按钮结束会话时才会失效   。
  - (3)Path属性：定义了Web站点上可以访问该Cookie的目录 [3]  。
  - (4)Domain属性：指定了可以访问该 Cookie 的 Web 站点或域。Cookie 机制并未遵循严格的同源策略，允许一个子域可以设置或获取其父域的 Cookie。当需要实现单点登录方案时，Cookie 的上述特性非常有用，然而也增加了 Cookie受攻击的危险，比如攻击者可以借此发动会话定置攻击。因而，浏览器禁止在 Domain 属性中设置.org、.com 等通用顶级域名、以及在国家及地区顶级域下注册的二级域名，以减小攻击发生的范围   。
  - (5)Secure属性：指定是否使用HTTPS安全协议发送Cookie。使用HTTPS安全协议，可以保护Cookie在浏览器和Web服务器间的传输过程中不被窃取和篡改。该方法也可用于Web站点的身份鉴别，即在HTTPS的连接建立阶段，浏览器会检查Web网站的SSL证书的有效性。但是基于兼容性的原因（比如有些网站使用自签署的证书）在检测到SSL证书无效时，浏览器并不会立即终止用户的连接请求，而是显示安全风险信息，用户仍可以选择继续访问该站点。由于许多用户缺乏安全意识，因而仍可能连接到Pharming攻击所伪造的网站   。
  - (6)HTTPOnly 属性 ：用于防止客户端脚本通过document.cookie属性访问Cookie，有助于保护Cookie不被跨站脚本攻击窃取或篡改。但是，HTTPOnly的应用仍存在局限性，一些浏览器可以阻止客户端脚本对Cookie的读操作，但允许写操作；此外大多数浏览器仍允许通过XMLHTTP对象读取HTTP响应中的Set-Cookie头  。