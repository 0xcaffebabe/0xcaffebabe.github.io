---
layout: post
title:  "首次登陆CentOS以及man page求助"
date:   2018-03-27T09:26:09
category: LINUX
tags: [LINUX]
---

首次登陆CentOS以及man page求助

<p>使用了Xshell自动填写账号密码登录：</p><pre class="brush:bash;toolbar:false">Last&nbsp;login:&nbsp;Mon&nbsp;Mar&nbsp;26&nbsp;20:23:10&nbsp;2018&nbsp;from&nbsp;192.168.133.1
[root@localhost&nbsp;~]#</pre><p>不知道命令怎么用？没关心，求助man吧！</p><pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;man&nbsp;man</pre><pre class="brush:bash;toolbar:false">man(1)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;General&nbsp;Commands&nbsp;Manual&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;man(1)

NAME
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;man&nbsp;-&nbsp;格式化并显示在线帮助手册页
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;manpath&nbsp;-&nbsp;定义用户查找man手册页的路径

总览
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;man&nbsp;&nbsp;[-acdfFhkKtwW]&nbsp;[-m&nbsp;系统名]&nbsp;[-p&nbsp;&lt;前处理程序&gt;]&nbsp;[-C&nbsp;&lt;配置文件&gt;]&nbsp;[-M&nbsp;&lt;路径&gt;]&nbsp;[-P&nbsp;&lt;浏览方式&gt;]&nbsp;[-S&nbsp;&lt;区段清单&gt;]&nbsp;[区段名称]&nbsp;帮助主题&nbsp;...

描述
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;man&nbsp;&nbsp;格式化并显示在线帮助手册页面。此版本支持&nbsp;MANPATH&nbsp;和&nbsp;（MAN）PAGER&nbsp;环境变量，因此，你可以拥有你自己的一系列&nbsp;man&nbsp;手册页并决定使用哪个程序来显示此格式的页面。如果定义了区段，&nbsp;man
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将只查找在指定区段内的文档。你也可以通过命令行或环境变量来指定查找区段&nbsp;&nbsp;&nbsp;的顺序和预定义将要执行的程序。如果主题中有“/”符号，则将其作为文件名的一部分处理&nbsp;&nbsp;&nbsp;，也就是说你可以用&nbsp;&nbsp;&nbsp;man
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;./foo.5&nbsp;也可以用&nbsp;man&nbsp;/cd/foo/bar.1.gz&nbsp;来查看各man&nbsp;文档。

选项
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-C&nbsp;配置文件
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;定义man.conf供使用；默认使用的是&nbsp;/etc/man.config&nbsp;。（参见&nbsp;man.conf(5)）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-M&nbsp;路径
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;定义一组查找man手册页的目录。如果没有指定此参数，系统环境变量&nbsp;&nbsp;MANPATH将被使用。&nbsp;&nbsp;如果查无到此环境变量，则按默认&nbsp;&nbsp;/etc/man.config&nbsp;&nbsp;文件中指定的查找。一个空的&nbsp;&nbsp;MANPATH&nbsp;&nbsp;子字
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;符串表示使用默认清单。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-P&nbsp;浏览方式
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;定义浏览的方式。此选项将覆盖&nbsp;&nbsp;MANPAGER&nbsp;&nbsp;环境变量（此变量将覆盖&nbsp;&nbsp;PAGER&nbsp;&nbsp;变量）。若不指定&nbsp;&nbsp;此参数，则使用&nbsp;&nbsp;&nbsp;MANPAGER&nbsp;&nbsp;&nbsp;或&nbsp;&nbsp;&nbsp;PAGER&nbsp;&nbsp;&nbsp;环境变量中的设置。此选项的预设的显示方式为
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/usr/bin/less-is。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-S&nbsp;区段清单
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该清单是一组用冒号分隔的欲查找的手册清单。此选项将覆盖&nbsp;&nbsp;MANSECT&nbsp;环境变量。&nbsp;有些指令或程序可能有一个以上的主题，它们位于不同的区段中。因此，要查看较后的区&nbsp;段，你可以在此指定
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;man&nbsp;查找区段的顺序。具体区段划分如下所示：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;区段1：用户指令
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;区段2：系统调用
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;区段3：程序库调用</pre><p>因为我使用了Xshell，才可以显示中文，如果是直接使用了终端机登录，可能看到的将是乱码。<br/></p>