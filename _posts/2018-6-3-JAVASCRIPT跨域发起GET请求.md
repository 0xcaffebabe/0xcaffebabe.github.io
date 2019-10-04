---
layout: post
title:  "JAVASCRIPT跨域发起GET请求"
date:   2018-06-03T11:48:53
category: JAVA
tags: [JAVA,WEB,网络]
---

JAVASCRIPT跨域发起GET请求

<p>众所周知，JavaScript因为浏览器的同源策略是有着跨域资源访问限制，那我们如何跨域发起一个get请求？</p><p>那就是用img script等元素进行。</p><p>使用JavaScript动态创建一个img元素，然后更新：<br/></p><pre class="brush:js;toolbar:false">	var&nbsp;img=document.createElement(&quot;img&quot;);
	img.src=&quot;http://www.baidu.com&quot;;
	document.appendChild(img);</pre><p>这样就对baidu发起了一个get请求，不过缺点显而易见，无法获取响应信息。<br/></p>