---
layout: post
title:  "说说JAVA当中的equals"
date:   2018-11-29T09:24:22
category: JAVA
tags: [JAVA]
---

说说JAVA当中的equals

<p>equals这个属于Object类的方法，几乎每天都在用，可是看着它，却是既熟悉，又陌生。</p><p>先来看看Object中的equals中写了什么：</p><pre><code>public boolean equals(Object obj) {<br>        return (this == obj);<br>}</code></pre><p>恩...似乎没有什么用，只是把当前对象的引用与传入的obj进行对比，于是，就会出现这么样的一个情况：</p><pre><code>String s1 = new String("1");<br>String s2 =new String("1");<br><br>System.err.println(s1 == s2);</code></pre><p>结果为false，就是因为s1与s2是不同的两个对象。</p><p>好，那么接下来来看看String是怎么重写equals方法的：</p><pre><code>public boolean equals(Object anObject) {<br>        if (this == anObject) {<br>            return true;<br>        }<br>        if (anObject instanceof String) {<br>            String aString = (String)anObject;<br>            if (coder() == aString.coder()) {<br>                return isLatin1() ? StringLatin1.equals(value, aString.value)<br>                                  : StringUTF16.equals(value, aString.value);<br>            }<br>        }<br>        return false;<br>}</code></pre><p>代码一大堆，但还是很好理解的，首先判断引用是否相同，其次判断是否属于String类，最后再判断字符序列。</p><p><span style="font-weight: bold;">所以，当需要比较两个对象的时候，需要重写equals方法。</span></p><p>那么重写equals时，一定得重写hashCode方法？<span style="font-weight: bold;"><br></span></p><p>那么hashCode又是什么？能吃吗？</p><p>hash，翻译过来又称哈希、散列，那么学过数据结构的都知道hash table是什么东西。</p><p>这里不深入讨论，回到equals，如果重写equals的同时不重写hashCode的时候，你的代码可能会出现一些莫名其妙的BUG。</p><p>来看一个例子：</p><p>假设有这么样的一个类：</p><pre><code>class Person{<br>        private String name;<br><br><br>        public Person(String name) {<br>            this.name = name;<br>        }<br><br>        @Override<br>        public boolean equals(Object obj) {<br>            if(obj instanceof  Person){<br>                Person person = (Person)obj;<br>                if(person.getName().equals(this.getName())){<br>                    return true;<br>                }<br>            }<br>            return false;<br>        }<br><br>        public String getName() {<br>            return name;<br>        }<br>    }</code></pre><p>这个Person类重写了equals方法，使用判断名字来判断两个对象是否相等。</p><p>我们使用一个哈希表来储存Person与年龄的映射关系：</p><pre><code>Map&lt;Person,Integer&gt; map = new HashMap&lt;&gt;();</code></pre><p>向map当中放入两个人：</p><pre><code>map.put(new Person("小明"),25);<br>    <br>map.put(new Person("小红"),18);</code></pre><p>下面一段代码的预期值为25：</p><pre><code>System.out.println(map.get(new Person("小明")));</code></pre><p>但是结果却为null，为什么？</p><p>原因就是在HashMap当中判断两个对象相等，是通过hashCode进行的，这是一个需要注意的点。</p><style>
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