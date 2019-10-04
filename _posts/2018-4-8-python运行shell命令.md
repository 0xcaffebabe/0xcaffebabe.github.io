---
layout: post
title:  "python运行shell命令"
date:   2018-04-08T02:02:05
category: PYTHON
tags: [PYTHON,LINUX]
---

python运行shell命令

<pre class="brush:python;toolbar:false">import&nbsp;os

ret&nbsp;=&nbsp;os.popen(&quot;date&quot;).read()

print(ret)</pre><p>先导入os模块，然后通过popen方法执行shell命令，并通过read方法读取执行结果，最后打印输出。</p><pre class="brush:bash;toolbar:false">[root@iZputslk1bvy2iZ&nbsp;~]#&nbsp;python&nbsp;test.py&nbsp;
Sat&nbsp;Apr&nbsp;&nbsp;7&nbsp;13:00:33&nbsp;CST&nbsp;2018</pre><p><br/></p>