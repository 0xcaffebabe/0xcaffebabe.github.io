---
layout: post
title:  "linux下实时监控tomcat日志"
date:   2018-04-15T12:02:35
category: LINUX
tags: [LINUX,WEB]
---

linux下实时监控tomcat日志

<p>到tomcat的日志目录下：</p><pre class="brush:bash;toolbar:false">[root@iZputslk1bvy2iZ&nbsp;~]#&nbsp;cd&nbsp;/home/apache-tomcat-8.5.29/logs/</pre><p>执行：</p><pre class="brush:bash;toolbar:false">[root@iZputslk1bvy2iZ&nbsp;logs]#&nbsp;tail&nbsp;-f&nbsp;catalina.out</pre><pre class="brush:bash;toolbar:false">[root@iZputslk1bvy2iZ&nbsp;logs]#&nbsp;tail&nbsp;-f&nbsp;catalina.out
...此处省略
14-Apr-2018&nbsp;21:17:06.973&nbsp;INFO&nbsp;[main]
&nbsp;org.apache.catalina.startup.Catalina.start&nbsp;Server&nbsp;startup&nbsp;in&nbsp;2391&nbsp;ms
[14,&nbsp;13,&nbsp;12,&nbsp;11,&nbsp;10,&nbsp;9,&nbsp;8]
[14,&nbsp;13,&nbsp;12,&nbsp;11,&nbsp;10,&nbsp;9,&nbsp;8]
50</pre><p>按ctrl+c退出<br/></p>