---
layout: post
title:  "JAVASCRIPT遍历某一元素的所有子元素"
date:   2018-05-18T00:01:42
category: WEB
tags: [WEB,JAVASCRIPT]
---

JAVASCRIPT遍历某一元素的所有子元素

<p>HTML代码：</p><pre class="brush:html;toolbar:false">&lt;ul&nbsp;id=&quot;menu&quot;&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;&lt;a&nbsp;href=&quot;http://www.baidu.com&quot;&gt;1&lt;/a&gt;&lt;/li&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;2&lt;/li&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;3&lt;/li&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/ul&gt;</pre><p>JavaScript代码：</p><pre class="brush:js;toolbar:false">var&nbsp;menu=document.getElementById(&quot;menu&quot;);
&nbsp;&nbsp;&nbsp;&nbsp;for(var&nbsp;i=0,len=menu.childNodes.length;i&lt;len;i++){
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(menu.childNodes[i].nodeType==1){
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;menu.childNodes[i].style=&quot;background-color:yellow&quot;;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;}</pre><p>先通过ID获取到父元素。</p><p>然后通过childnodes来进行遍历，当元素类型=1时（类型为元素），运行结果如下：</p><p><img src="https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1526526015967.png"/></p>