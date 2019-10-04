---
layout: post
title:  "linux下安装pip"
date:   2018-03-29T23:25:50
category: PYTHON
tags: [PYTHON,LINUX]
---

linux下安装pip

<p>这篇文章假设在你已经安装好python环境的情况下。</p><p>首先</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;wget&nbsp;https://bootstrap.pypa.io/get-pip.py</pre><p>回车</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;wget&nbsp;https://bootstrap.pypa.io/get-pip.py
--2018-03-29&nbsp;10:21:09--&nbsp;&nbsp;https://bootstrap.pypa.io/get-pip.py
正在解析主机&nbsp;bootstrap.pypa.io&nbsp;(bootstrap.pypa.io)...&nbsp;151.101.228.175
正在连接&nbsp;bootstrap.pypa.io&nbsp;(bootstrap.pypa.io)|151.101.228.175|:443...&nbsp;已连接。
已发出&nbsp;HTTP&nbsp;请求，正在等待回应...&nbsp;200&nbsp;OK
长度：1780465&nbsp;(1.7M)&nbsp;[text/x-python]
正在保存至:&nbsp;“get-pip.py”

get-pip.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;100%[===================&gt;]&nbsp;&nbsp;&nbsp;1.70M&nbsp;&nbsp;1.09MB/s&nbsp;&nbsp;用时&nbsp;1.6s&nbsp;&nbsp;&nbsp;&nbsp;

2018-03-29&nbsp;10:21:12&nbsp;(1.09&nbsp;MB/s)&nbsp;-&nbsp;已保存&nbsp;“get-pip.py”&nbsp;[1780465/1780465])</pre><p>下载完成，然后使用执行这个.py文件。</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;python&nbsp;get-pip.py</pre><p>程序就会自动安装好pip了。时间可能有点长，请耐心等待</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;python&nbsp;get-pip.py&nbsp;
Collecting&nbsp;pip
&nbsp;&nbsp;Downloading&nbsp;pip-9.0.3-py2.py3-none-any.whl&nbsp;(1.4MB)
&nbsp;&nbsp;&nbsp;&nbsp;100%&nbsp;|████████████████████████████████|&nbsp;1.4MB&nbsp;13kB/s&nbsp;
Installing&nbsp;collected&nbsp;packages:&nbsp;pip
&nbsp;&nbsp;Found&nbsp;existing&nbsp;installation:&nbsp;pip&nbsp;9.0.1
&nbsp;&nbsp;&nbsp;&nbsp;Uninstalling&nbsp;pip-9.0.1:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Successfully&nbsp;uninstalled&nbsp;pip-9.0.1
Successfully&nbsp;installed&nbsp;pip-9.0.3</pre><p>安装成功。<br/></p>