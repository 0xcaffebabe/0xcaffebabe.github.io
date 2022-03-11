---
layout: post
title:  "JAVASCRIPT动态加载js文件"
date:   2018-05-19T06:17:58
category: WEB
tags: [WEB,JAVASCRIPT]
---

JAVASCRIPT动态加载js文件

<p>核心方法：createElement</p><p>通过createElement动态创建一个元素，并修改它的属性，最终把它加入到documet.body的子节点里。<br/></p><p>index.html代码：</p><pre class="brush:js;toolbar:false">var&nbsp;script=document.createElement(&quot;script&quot;);
&nbsp;&nbsp;&nbsp;&nbsp;script.src=&quot;a.js&quot;;
&nbsp;&nbsp;&nbsp;&nbsp;document.body.appendChild(script);</pre><p>a.js代码：</p><pre class="brush:js;toolbar:false">function&nbsp;test(){
&nbsp;&nbsp;&nbsp;&nbsp;alert(&quot;hello,world&quot;);
}
test();</pre><p>运行结果肯定是hello,world啦！<br/></p>