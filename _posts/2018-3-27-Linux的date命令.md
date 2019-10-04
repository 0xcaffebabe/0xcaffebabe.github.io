---
layout: post
title:  "Linux的date命令"
date:   2018-03-27T09:34:34
category: LINUX
tags: [LINUX]
---

Linux的date命令

<pre class="brush:bash;toolbar:false">[root@localhost&nbsp;~]#&nbsp;date
2018年&nbsp;03月&nbsp;26日&nbsp;星期一&nbsp;20:29:58&nbsp;CST
[root@localhost&nbsp;~]#&nbsp;date&nbsp;+%y/%m/%d
18/03/26</pre><p>date的man page：</p><pre class="brush:bash;toolbar:false">DATE(1)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FSF&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DATE(1)

NAME
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;date&nbsp;-&nbsp;打印或设置系统日期和时间

总览
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;date&nbsp;[选项]...&nbsp;[+格式]
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;date&nbsp;[选项]&nbsp;[MMDDhhmm[[CC]YY][.ss]]

描述
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;根据指定格式显示当前时间或设置系统时间.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-d,&nbsp;--date=STRING
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;显示由&nbsp;STRING&nbsp;指定的时间,&nbsp;而不是当前时间

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-f,&nbsp;--file=DATEFILE
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;显示&nbsp;DATEFILE&nbsp;中每一行指定的时间,&nbsp;如同将&nbsp;DATEFILE&nbsp;中的每行作为&nbsp;--date&nbsp;的参数一样

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-I,&nbsp;--iso-8601[=TIMESPEC]&nbsp;按照&nbsp;ISO-8601&nbsp;的日期/时间格式输出时间.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TIMESPEC=`date&#39;&nbsp;(或者不指定时)仅输出日期,等于&nbsp;`hours&#39;,&nbsp;`minutes&#39;,&nbsp;或`seconds&#39;&nbsp;时按照指定精度输出日期及时间.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-r,&nbsp;--reference=FILE
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;显示&nbsp;FILE&nbsp;的最后修改时间

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-R,&nbsp;--rfc-822
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;根据&nbsp;RFC-822&nbsp;指定格式输出日期

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-s,&nbsp;--set=STRING
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;根据&nbsp;STRING&nbsp;设置时间

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-u,&nbsp;--utc,&nbsp;--universal
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;显示或设置全球时间(格林威治时间)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--help&nbsp;显示本帮助文件并退出

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--version
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;显示版本信息并退出

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;格式&nbsp;FORMAT&nbsp;控制着输出格式.&nbsp;仅当选项指定为全球时间时本格式才有效。&nbsp;分别解释如下:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%%&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;文本的&nbsp;%

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%a&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当前区域的星期几的简写&nbsp;(Sun..Sat)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当前区域的星期几的全称&nbsp;(不同长度)&nbsp;(Sunday..Saturday)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%b&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当前区域的月份的简写&nbsp;(Jan..Dec)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%B&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当前区域的月份的全称(变长)&nbsp;(January..December)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%c&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当前区域的日期和时间&nbsp;(Sat&nbsp;Nov&nbsp;04&nbsp;12:02:33&nbsp;EST&nbsp;1989)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%d&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(月份中的)几号(用两位表示)&nbsp;(01..31)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%D&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;日期(按照&nbsp;月/日期/年&nbsp;格式显示)&nbsp;(mm/dd/yy)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%e&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(月份中的)几号(去零表示)&nbsp;(&nbsp;1..31)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%h&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;同&nbsp;%b

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%H&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;小时(按&nbsp;24&nbsp;小时制显示，用两位表示)&nbsp;(00..23)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%I&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;小时(按&nbsp;12&nbsp;小时制显示，用两位表示)&nbsp;(01..12)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%j&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(一年中的)第几天(用三位表示)&nbsp;(001..366)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%k&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;小时(按&nbsp;24&nbsp;小时制显示，去零显示)&nbsp;(&nbsp;0..23)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;小时(按&nbsp;12&nbsp;小时制显示，去零表示)&nbsp;(&nbsp;1..12)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%m&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;月份(用两位表示)&nbsp;(01..12)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%M&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;分钟数(用两位表示)&nbsp;(00..59)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%n&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;换行

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%p&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当前时间是上午&nbsp;AM&nbsp;还是下午&nbsp;PM

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%r&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;时间,按&nbsp;12&nbsp;小时制显示&nbsp;(hh:mm:ss&nbsp;[A/P]M)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%s&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;从&nbsp;1970年1月1日0点0分0秒到现在历经的秒数&nbsp;(GNU扩充)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%S&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;秒数(用两位表示)(00..60)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%t&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;水平方向的&nbsp;tab&nbsp;制表符

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%T&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;时间,按&nbsp;24&nbsp;小时制显示(hh:mm:ss)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%U&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(一年中的)第几个星期，以星期天作为一周的开始(用两位表示)&nbsp;(00..53)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%V&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(一年中的)第几个星期，以星期一作为一周的开始(用两位表示)&nbsp;(01..52)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%w&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;用数字表示星期几&nbsp;(0..6);&nbsp;0&nbsp;代表星期天

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%W&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(一年中的)第几个星期，以星期一作为一周的开始(用两位表示)&nbsp;(00..53)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%x&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;按照&nbsp;(mm/dd/yy)&nbsp;格式显示当前日期

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%X&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;按照&nbsp;(%H:%M:%S)&nbsp;格式显示当前时间

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;年的后两位数字&nbsp;(00..99)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%Y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;年(用&nbsp;4&nbsp;位表示)&nbsp;(1970...)</pre><p>参数很多，无需记忆，需要的时候直接查找文档吧。<br/></p>