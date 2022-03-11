---
layout: post
title:  "kali linux使用Nmap扫描目标主机操作系统类型"
date:   2018-03-30T05:28:58
category: LINUX
tags: [LINUX,KALI]
---

kali linux使用Nmap扫描目标主机操作系统类型

<p>语法：</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;nmap&nbsp;-O&nbsp;主机IP</pre><p>-O ：显示目标主机操作系统信息</p><pre class="brush:bash;toolbar:false">root@bogon:~#&nbsp;nmap&nbsp;-O&nbsp;www.ismy.wang</pre><p>扫描自己的主机，结果如下：</p><pre class="brush:bash;toolbar:false">Running:&nbsp;Actiontec&nbsp;embedded,&nbsp;Linux&nbsp;2.4.X|3.X,&nbsp;Microsoft&nbsp;Windows&nbsp;XP|7|2012</pre><p>结果仅供参考，不一定准确。<br/></p>