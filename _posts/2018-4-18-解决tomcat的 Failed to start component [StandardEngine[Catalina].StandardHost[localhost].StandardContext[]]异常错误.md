---
layout: post
title:  "解决tomcat的 Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[]]异常错误"
date:   2018-04-18T11:01:11
category: JAVA
tags: [JAVA,WEB]
---

解决tomcat的 Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[]]异常错误

<p>部署web项目的时候，报了这样的一个错误：</p><pre class="brush:java;toolbar:false">java.lang.IllegalStateException:&nbsp;ContainerBase.addChild:&nbsp;
start:&nbsp;org.apache.catalina.LifecycleException:&nbsp;
Failed&nbsp;to&nbsp;start&nbsp;component&nbsp;[StandardEngine[Catalina].StandardHost[localhost].StandardContext[]]</pre><p>百度无果后，仔细看了下日志：</p><pre class="brush:java;toolbar:false">&nbsp;Invalid&nbsp;&lt;url-pattern&gt;&nbsp;[TableDetail]&nbsp;in&nbsp;servlet&nbsp;mapping</pre><p>想起刚创建了一个servlet，看了一下，原来是servlet的urlPatterns少了一个/，</p><p>添加后，正常运行。</p><p>看来有时候除了错误不能光想着搜索解决问题，还是好好看看日志再说。<br/></p><p><br/></p><p><br/></p>