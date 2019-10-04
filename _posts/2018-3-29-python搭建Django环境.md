---
layout: post
title:  "python搭建Django环境"
date:   2018-03-29T06:02:20
category: PYTHON
tags: [PYTHON,WEB]
---

python搭建Django环境

<p>这篇文章假设在你已经安装了python以及安装了pip等工具的基础上。</p><p>首先</p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;pip&nbsp;install&nbsp;Django</pre><p>回车过后</p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;pip&nbsp;install&nbsp;Django
Collecting&nbsp;Django
&nbsp;&nbsp;Downloading&nbsp;Django-1.11.11-py2.py3-none-any.whl&nbsp;(6.9MB)
&nbsp;&nbsp;&nbsp;&nbsp;100%&nbsp;|████████████████████████████████|&nbsp;7.0MB&nbsp;67kB/s&nbsp;
Collecting&nbsp;pytz&nbsp;(from&nbsp;Django)
&nbsp;&nbsp;Downloading&nbsp;pytz-2018.3-py2.py3-none-any.whl&nbsp;(509kB)
&nbsp;&nbsp;&nbsp;&nbsp;100%&nbsp;|████████████████████████████████|&nbsp;512kB&nbsp;250kB/s&nbsp;
Installing&nbsp;collected&nbsp;packages:&nbsp;pytz,&nbsp;Django
Successfully&nbsp;installed&nbsp;Django-1.11.11&nbsp;pytz-2018.3</pre><p>已经安装完成了。</p><p>测试：</p><pre class="brush:bash;toolbar:false">&gt;&gt;&gt;&nbsp;import&nbsp;django</pre><p>没有出错的话就代表安装成功了。<br/></p>