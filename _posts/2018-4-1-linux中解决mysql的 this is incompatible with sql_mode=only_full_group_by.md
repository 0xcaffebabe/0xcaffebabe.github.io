---
layout: post
title:  "linux中解决mysql的 this is incompatible with sql_mode=only_full_group_by"
date:   2018-04-01T10:58:53
category: MYSQL
tags: [MYSQL,WEB]
---

linux中解决mysql的 this is incompatible with sql_mode=only_full_group_by

<p>好吧，换了服务器问题还挺多的。</p><p>中午的时候服务器抛了一个异常：</p><pre class="brush:java;toolbar:false">com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException:&nbsp;
Expression&nbsp;#2&nbsp;of&nbsp;SELECT&nbsp;list&nbsp;is&nbsp;not&nbsp;in&nbsp;GROUP&nbsp;BY&nbsp;clause&nbsp;and&nbsp;contains&nbsp;nonaggregated&nbsp;column
&nbsp;&#39;blog.log.brower&#39;&nbsp;which&nbsp;is&nbsp;not&nbsp;functionally&nbsp;dependent&nbsp;on&nbsp;columns&nbsp;in&nbsp;GROUP&nbsp;BY&nbsp;clause;&nbsp;
&nbsp;this&nbsp;is&nbsp;incompatible&nbsp;with&nbsp;sql_mode=only_full_group_by</pre><p>就按网上的方法：</p><pre class="brush:sql;toolbar:false">set&nbsp;@@GLOBAL.sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,
ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION</pre><p>起作用了，但晚上改服务器字符集重启了一下mysql，又给还原了，这不是办法。</p><p>于是就在配置文件(/etc/my.cnf)的[mysqld]节点中加上：</p><pre class="brush:sql;toolbar:false">sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,
NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION</pre><p>问题解决！<br/></p>