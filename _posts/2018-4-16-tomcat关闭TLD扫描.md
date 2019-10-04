---
layout: post
title:  "tomcat关闭TLD扫描"
date:   2018-04-16T07:08:48
category: WEB
tags: [WEB]
---

tomcat关闭TLD扫描

<p>有时候在启动tomcat 的时候，日志中会显示tomcat在进行tld扫描，这可能需要很长的一段时间，那么要如何关闭？</p><p>只需把tomcat的conf目录下的context.xml改一下：</p><p>在Context节点中，加上属性：processTlds=&quot;false&quot;。</p><p>加完之后是这个样子的：</p><pre class="brush:xml;toolbar:false">&lt;Context&nbsp;processTlds=&quot;false&quot;&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;WatchedResource&gt;WEB-INF/web.xml&lt;/WatchedResource&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;WatchedResource&gt;${catalina.base}/conf/web.xml&lt;/WatchedResource&gt;
&lt;/Context&gt;</pre><p><br/></p>