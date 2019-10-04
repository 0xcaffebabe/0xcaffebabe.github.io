---
layout: post
title:  "linux解决mysql插入数据中文乱码问题"
date:   2018-04-01T10:32:22
category: LINUX
tags: [LINUX,MYSQL]
---

linux解决mysql插入数据中文乱码问题

<p>今天服务器刚完成windows向linux 的转变，刚开始了第一篇博文，就发现了插入中文后变成了乱码，于是就</p><pre class="brush:sql;toolbar:false">&nbsp;SHOW&nbsp;VARIABLES&nbsp;LIKE&nbsp;&#39;character%&#39;;</pre><p>发现编码不一致，有的是utf8，有的是lanti1，</p><p>就一个个set改，后来发现也没用，百度上找了一下说要到配置文件的[mysqld]节点下增加default-character-set=utf8，但是重启mysql的时候报错：unknown variable &#39;default-character-set=utf8&#39;，没办法，继续找办法，最终发现，把default-character-set=utf8改为default_character_server即可</p>