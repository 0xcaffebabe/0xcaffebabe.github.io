---
layout: post
title:  "JAVA对web发起POST请求"
date:   2018-04-19T08:14:58
category: JAVA
tags: [JAVA,WEB]
---

JAVA对web发起POST请求

<pre class="brush:java;toolbar:false">public&nbsp;static&nbsp;void&nbsp;main(String[]&nbsp;args)&nbsp;throws&nbsp;IOException&nbsp;{
&nbsp;&nbsp;&nbsp;System.err.println(&nbsp;WebUtil.sendPost(&quot;http://localhost/Test&quot;,&quot;params1=123&amp;params=56&quot;,null));
}

public&nbsp;static&nbsp;String&nbsp;sendPost(String&nbsp;url,String&nbsp;param,HashMap&lt;String,String&gt;&nbsp;requestHead)&nbsp;
throws&nbsp;IOException&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;URL&nbsp;url1=new&nbsp;URL(url);
&nbsp;&nbsp;&nbsp;&nbsp;URLConnection&nbsp;connection=url1.openConnection();
&nbsp;&nbsp;&nbsp;&nbsp;connection.setRequestProperty(&quot;Connection&quot;,&quot;Keep-Alive&quot;);
&nbsp;&nbsp;&nbsp;&nbsp;if(requestHead==null){
&nbsp;&nbsp;&nbsp;&nbsp;}else{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for(String&nbsp;key:requestHead.keySet()){
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;connection.setRequestProperty(key,requestHead.get(key));
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;connection.setDoInput(true);
&nbsp;&nbsp;&nbsp;&nbsp;connection.setDoOutput(true);
&nbsp;&nbsp;&nbsp;&nbsp;PrintWriter&nbsp;printWriter=new&nbsp;PrintWriter(connection.getOutputStream());
&nbsp;&nbsp;&nbsp;&nbsp;printWriter.write(param);
&nbsp;&nbsp;&nbsp;&nbsp;printWriter.flush();
&nbsp;&nbsp;&nbsp;&nbsp;InputStream&nbsp;inputStream=connection.getInputStream();
&nbsp;&nbsp;&nbsp;&nbsp;int&nbsp;len=0;
&nbsp;&nbsp;&nbsp;&nbsp;ByteArrayOutputStream&nbsp;outputStream=new&nbsp;ByteArrayOutputStream();
&nbsp;&nbsp;&nbsp;&nbsp;byte[]&nbsp;bytes=new&nbsp;byte[024];
&nbsp;&nbsp;&nbsp;&nbsp;while((len=inputStream.read(bytes))!=-1){
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;outputStream.write(bytes);
&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;String&nbsp;ret=new&nbsp;String(outputStream.toByteArray());
&nbsp;&nbsp;&nbsp;&nbsp;String&nbsp;charset=getWebCharset(ret);
&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;new&nbsp;String(outputStream.toByteArray(),charset);
}</pre><p>其中要注意最重要的两行：</p><pre class="brush:java;toolbar:false">&nbsp;connection.setDoInput(true);
&nbsp;connection.setDoOutput(true);</pre><p>运行结果：</p><p>params1||{123}<br/>params||{56}</p>