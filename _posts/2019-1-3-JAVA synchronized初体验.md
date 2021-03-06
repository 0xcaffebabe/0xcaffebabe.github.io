---
layout: post
title:  "JAVA synchronized初体验"
date:   2019-01-03T08:22:25
category: JAVA
tags: [JAVA]
---

JAVA synchronized初体验

<p>先来看看synchronized这个关键字是什么意思：</p><p><img src="https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1546423168640.png" style="max-width:100%;"><br></p><p>同步，同步什么？</p><p>要同步的就是这个关键字后面紧跟的花括号里的代码，也就是代码块。</p><p>为什么要同步？</p><p>来看一个例子：</p><pre><code>public static int i=0;<br>    public static void main(String[] args) throws InterruptedException {<br><br><br>        var t1=new Thread(()-&gt;{<br><br>            for (int i1 = 0; i1 &lt; 10000; i1++) {<br><br>                i++;<br>            }<br>        });<br><br>        var t2 = new Thread(()-&gt;{<br><br>            for (int i1 = 0; i1 &lt; 10000; i1++) {<br><br>                i++;<br>            }<br>        });<br><br>        t1.start();<br>        t2.start();<br>        t1.join();<br>        t2.join();<br><br><br>        System.out.println(i);<br>    }</code></pre><p>这段代码理论上最后输出的i的值应该是20000，</p><p>但是本次运行之后的结果却是17146，为什么？</p><p>网上的相关说明有很多，总结一下就是一段线程代码运行到一半，这时候线程调度器又跑去运行另外一个线程，导致线程内存中所做的修改没来得及刷新到主内存，从而导致数据不一致。</p><p>这个时候，就轮到我们的主角登场了，synchronized关键字的作用就是锁住某一个对象，当这个对象没被解锁之前，别的线程无法锁住这个对象。</p><p>那么，我们来尝试一下：</p><p>&nbsp;这是修改之后的部分代码：<br></p><pre><code>var t1=new Thread(()-&gt;{<br><br>            synchronized (Main1.class){<br>                for (int i1 = 0; i1 &lt; 10000; i1++) {<br><br>                    i++;<br>                }<br>            }<br>        });<br><br>        var t2 = new Thread(()-&gt;{<br><br>            synchronized (Main1.class){<br>                for (int i1 = 0; i1 &lt; 10000; i1++) {<br><br>                    i++;<br>                }    <br>            }<br>            <br>        });</code></pre><p>使用synchronized锁住了Main1.class这个对象，这样我们就能保证t1和t2能从头到尾完整地运行一遍，不会出现之前那样的情况。</p><p>无论运行多少遍，结果肯定为20000</p><style>
<!--
 /* Font Definitions */
 @font-face
	{font-family:Helvetica;
	panose-1:2 11 6 4 2 2 2 2 2 4;
	mso-font-charset:0;
	mso-generic-font-family:swiss;
	mso-font-pitch:variable;
	mso-font-signature:-536858881 -1073711013 9 0 511 0;}
@font-face
	{font-family:"Cambria Math";
	panose-1:2 4 5 3 5 4 6 3 2 4;
	mso-font-charset:0;
	mso-generic-font-family:roman;
	mso-font-pitch:variable;
	mso-font-signature:3 0 0 0 1 0;}
@font-face
	{font-family:等线;
	panose-1:2 1 6 0 3 1 1 1 1 1;
	mso-font-alt:DengXian;
	mso-font-charset:134;
	mso-generic-font-family:auto;
	mso-font-pitch:variable;
	mso-font-signature:-1610612033 953122042 22 0 262159 0;}
@font-face
	{font-family:"\@等线";
	panose-1:2 1 6 0 3 1 1 1 1 1;
	mso-font-charset:134;
	mso-generic-font-family:auto;
	mso-font-pitch:variable;
	mso-font-signature:-1610612033 953122042 22 0 262159 0;}
 /* Style Definitions */
 p.MsoNormal, li.MsoNormal, div.MsoNormal
	{mso-style-unhide:no;
	mso-style-qformat:yes;
	mso-style-parent:"";
	margin:0cm;
	margin-bottom:.0001pt;
	text-align:justify;
	text-justify:inter-ideograph;
	mso-pagination:none;
	font-size:10.5pt;
	mso-bidi-font-size:11.0pt;
	font-family:等线;
	mso-ascii-font-family:等线;
	mso-ascii-theme-font:minor-latin;
	mso-fareast-font-family:等线;
	mso-fareast-theme-font:minor-fareast;
	mso-hansi-font-family:等线;
	mso-hansi-theme-font:minor-latin;
	mso-bidi-font-family:"Times New Roman";
	mso-bidi-theme-font:minor-bidi;
	mso-font-kerning:1.0pt;}
.MsoChpDefault
	{mso-style-type:export-only;
	mso-default-props:yes;
	font-family:等线;
	mso-bidi-font-family:"Times New Roman";
	mso-bidi-theme-font:minor-bidi;}
 /* Page Definitions */
 @page
	{mso-page-border-surround-header:no;
	mso-page-border-surround-footer:no;}
@page WordSection1
	{size:612.0pt 792.0pt;
	margin:72.0pt 90.0pt 72.0pt 90.0pt;
	mso-header-margin:36.0pt;
	mso-footer-margin:36.0pt;
	mso-paper-source:0;}
div.WordSection1
	{page:WordSection1;}
-->
</style>