---
layout: post
title:  "XSS防御：使用HttpOnly"
date:   2018-05-05T11:04:41
category: JAVA
tags: [JAVA,WEB,网络]
---

XSS防御：使用HttpOnly

<p>HTTPonly解决的事XSS攻击的cookie劫持问题。</p><p>那么如何添加？</p><p>只需在cookie的值加上HTTPonly即可，如：</p><pre class="brush:html;toolbar:false">cookiename=value;HTTPOnly</pre><p>值得注意的是，HTTPonly可以只对部分cookie键值对起作用。<br/></p>