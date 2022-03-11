---
layout: post
title:  "linux安装tomcat"
date:   2018-04-01T11:00:47
category: JAVA
tags: [JAVA,LINUX,WEB]
---

linux安装tomcat

<p>首先到tomcat官网：<a href="http://tomcat.apache.org/">http://tomcat.apache.org/</a><br/></p><p>找到下载专区：</p><p><img src="http://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1522500494346.png"/></p><p>复制tar.gz下载链接：</p><p><img src="http://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1522500502031.png"/></p><p>输入如下命令：</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;wget&nbsp;http://mirror.bit.edu.cn/apache/tomcat/tomcat-9/v9.0.6/bin/apache-tomcat-9.0.6.tar.gz</pre><p>回车。</p><p>等待下载完成。</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;wget&nbsp;http://mirror.bit.edu.cn/apache/tomcat/tomcat-9/v9.0.6/bin/apache-tomcat-9.0.6.tar.gz
--2018-03-31&nbsp;20:50:34--&nbsp;&nbsp;http://mirror.bit.edu.cn/apache/tomcat/tomcat-9/v9.0.6/bin/apache-tomcat-9.0.6.tar.gz
正在解析主机&nbsp;mirror.bit.edu.cn&nbsp;(mirror.bit.edu.cn)...&nbsp;202.204.80.77
正在连接&nbsp;mirror.bit.edu.cn&nbsp;(mirror.bit.edu.cn)|202.204.80.77|:80...&nbsp;已连接。
已发出&nbsp;HTTP&nbsp;请求，正在等待回应...&nbsp;200&nbsp;OK
长度：9494739&nbsp;(9.1M)&nbsp;[application/octet-stream]
正在保存至:&nbsp;“apache-tomcat-9.0.6.tar.gz”

apache-tomcat-9.0.6.tar.gz
&nbsp;&nbsp;9.05M&nbsp;&nbsp;&nbsp;243KB/s&nbsp;&nbsp;用时&nbsp;24s&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

2018-03-31&nbsp;20:50:58&nbsp;(392&nbsp;KB/s)&nbsp;-&nbsp;已保存&nbsp;“apache-tomcat-9.0.6.tar.gz”&nbsp;[9494739/9494739])</pre><p>解压缩：</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;tar&nbsp;-xzf&nbsp;apache-tomcat-9.0.6.tar.gz</pre><p>完成，进入目录下的bin中，执行startup.sh</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;cd&nbsp;./apache-tomcat-9.0.6/bin
root@bogon:~/apache-tomcat-9.0.6/bin#&nbsp;./startup.sh&nbsp;
Using&nbsp;CATALINA_BASE:&nbsp;&nbsp;&nbsp;/root/apache-tomcat-9.0.6
Using&nbsp;CATALINA_HOME:&nbsp;&nbsp;&nbsp;/root/apache-tomcat-9.0.6
Using&nbsp;CATALINA_TMPDIR:&nbsp;/root/apache-tomcat-9.0.6/temp
Using&nbsp;JRE_HOME:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/usr
Using&nbsp;CLASSPATH:
/root/apache-tomcat-9.0.6/bin/bootstrap.jar:/root/apache-tomcat-9.0.6/bin/tomcat-juli.jar
Tomcat&nbsp;started.</pre><p>注意要开放相关端口才能访问。<br/></p>