---
layout: post
title:  "JAVASCRIPT动态创建样式表"
date:   2018-05-21T23:20:11
category: WEB
tags: [WEB,JAVASCRIPT]
---

JAVASCRIPT动态创建样式表

<p>index.html：</p><pre class="brush:js;toolbar:false">var&nbsp;link=document.createElement(&quot;link&quot;);
&nbsp;&nbsp;&nbsp;&nbsp;link.href=&quot;style.css&quot;;
&nbsp;&nbsp;&nbsp;&nbsp;link.rel=&quot;stylesheet&quot;;
&nbsp;&nbsp;&nbsp;&nbsp;link.type=&quot;text/css&quot;;
&nbsp;&nbsp;&nbsp;&nbsp;document.head.appendChild(link);</pre><p>style.css：</p><pre class="brush:css;toolbar:false;">body{
&nbsp;&nbsp;&nbsp;&nbsp;background-color:&nbsp;black;
}</pre><p>运行结果：</p><p><img src="https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1526869178797.png"/></p>