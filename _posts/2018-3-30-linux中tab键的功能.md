---
layout: post
title:  "linux中tab键的功能"
date:   2018-03-30T11:28:49
category: LINUX
tags: [LINUX]
---

linux中tab键的功能

<p>在linux的bash中，tab键可被用来补全命令或者文件名。</p><p>假设你要用到一个你只记住前面几个字母的命令，那么tab键就派上用场了，比如：<br/></p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;ipt</pre><p>这时候你突然忘了后面是什么了，没关系，只需按一下tab键：</p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;ipt
iptables&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iptables-restore&nbsp;&nbsp;iptables-save&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iptables-xml&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iptunnel</pre><p>此时，若只有一个选项，命令就会自动补全，若有多个选项，系统就会给你列出所有选项。</p><p>另外，tab的另外一个功能就是补全文件名或者文件路径，用法和上面一样：</p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;cd&nbsp;ap</pre><p>按下tab：</p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;cd&nbsp;apache-tomcat-9.0.6/</pre><p>自动给你补全了。<br/></p>