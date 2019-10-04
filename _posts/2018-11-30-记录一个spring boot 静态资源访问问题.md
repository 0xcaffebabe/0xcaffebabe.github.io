---
layout: post
title:  "记录一个spring boot 静态资源访问问题"
date:   2018-11-30T04:21:52
category: JAVA
tags: [JAVA]
---

记录一个spring boot 静态资源访问问题

<p>spring boot 只要把静态资源放在static目录下，理论是可以直接访问的。</p><p>但是，今天却发现了一个很是头疼的问题，静态资源放入static文件夹了，但通过浏览器却是访问不到。</p><p>网上搜索了一大堆，都是一份文章你抄来，他抄去，一点价值都没有。</p><p>于是回到控制台，仔细查看spring boot 启动时输出的日志信息：</p><p><img src="https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1543472454965.png" style="max-width:100%;"><br></p><p>发现spring boot并没有对这个URL做映射，这应该是我做了什么自定义配置导致的spring boot 默认的自动配置被替换掉了。</p><p>于是把问题定位到了一个继承了WebMvcConfigurationSupport的java配置上：</p><pre><code>public class WebConfig extends WebMvcConfigurationSupport {<br><br>   <br>    @Override<br>    public void addInterceptors(InterceptorRegistry registry) {<br>        registry.addInterceptor(new HttpInterceptor());<br>    }<br><br><br>}</code></pre><p>有可能是这段代码导致的URL映射没自动进行。关掉这个配置，果然能从浏览器访问到静态资源了。</p><p>于是寻找这个配置添加资源映射的方法，找到了一个addResourceHandlers方法。</p><p>重载这个方法，搜索ResourceHandlerRegistry的用法：</p><pre><code>private static final String[] RESOURCE_LOCATIONS =<br>            { "classpath:/META-INF/resources/", "classpath:/resources/", "classpath:/static/", "classpath:/public/" };<br>    @Override<br>    protected void addResourceHandlers(ResourceHandlerRegistry registry) {<br>        try {<br><br>            File directiory = new File("");<br>            registry.addResourceHandler("/**").addResourceLocations(RESOURCE_LOCATIONS).addResourceLocations("file:" + directiory.getCanonicalPath() + "/");<br><br>        } catch (Exception e) {<br><br>        }<br><br>}</code></pre><p>添加之后，静态资源正常访问。</p><style>
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