---
layout: post
title:  "XSS攻击进阶：cookie盗取"
date:   2018-04-29T11:24
category: WEB
tags: [WEB]
---

XSS攻击进阶：cookie盗取

<p>上一篇文章写了三种XSS攻击类型，那么这一篇文章就来谈谈如何进行漏洞利用。</p><p>首先，我们知道，cookie一般加密了用户的登录凭证，换句话说，攻击者可以利用cookie直接登录受害者的账号：</p><pre class="brush:js;toolbar:false">var&nbsp;cookie=document.cookie;</pre><p>以上代码是获取当前页面的cookie，那如何发送这个cookie给受害者？</p><p>由于浏览器同源策略的限制，我们可以用img的src属性发起一个get请求，将cookie当做参数发送给远端服务器。</p><p>或者也可以使用xmlhttprequest发送一个请求，注意服务器要返回一个<span class="RichText CopyrightRichText-richText">Access-Control-Allow-Origin</span>响应头才能发起这个请求。</p>