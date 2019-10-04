---
layout: post
title:  "JavaScript识别浏览器"
date:   2018-05-02T10:09:44
category: WEB
tags: [WEB,JAVASCRIPT]
---

JavaScript识别浏览器

<p>一般来说，识别navigator.userAgent即可识别出用户所使用的浏览器，但是UA是可以伪造的。</p><p>我们的思路是根据各个浏览器的独特功能来识别浏览器，比如：</p><pre class="brush:js;toolbar:false">if(window.ActiveXObject){
&nbsp;&nbsp;&nbsp;&nbsp;//IE6或更低版本
}</pre><p>以上代码即可识别IE浏览器。<br/></p>