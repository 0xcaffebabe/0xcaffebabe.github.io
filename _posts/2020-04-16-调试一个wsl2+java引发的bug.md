---
layout: post
title:  "调试一个wsl2+java引发的bug"
date:   2020-04-16T016:00:00
category: 日常
tags: [日常]
---

java如何处理localhost这个主机名的?

# 调试一个wsl2+java引发的bug

最近听说wsl2将要在2004稳定可用，于是就赶了时髦在使用了wsl+docker部署了数据库和nacos等等东西，将原来使用虚拟机的容器都迁移过去

这迁移后就出了问题，目前（2020 04 16）wsl2是无法自定义ip地址，但是之前的版本更新已经可以将localhost的请求转发到wsl2里面去

当我部署完nacos之后，使用浏览器访问localhost:8848是没有问题的
但是问题就在于java客户端死活连接不上，java客户端使用的主机名就是localhost，报的是connection refuse

## 调试JDK源码

但是当我使用了wsl2内部提供的地址之后，socket连接成功了

```java
Socket socket = new Socket("localhost",8848); // 连接拒绝
Socket socket = new Socket("127.0.0.1",8848); // 连接拒绝
Socket socket = new Socket("172.30.39.169",8848);  // 连接正常
```

既然wsl官方都宣称可以使用localhost访问了，而且浏览器也确实可以访问

那么问题既有可能出现在java对localhost的解析上面

调试JDK源码发现，JDK 的InetAddress使用这段代码将主机名转为ip地址

```java
 try {
    addresses = nameService.lookupAllHostAddr(host);
} catch (UnknownHostException uhe) {
    if (host.equalsIgnoreCase("localhost")) {
        addresses = new InetAddress[] { impl.loopbackAddress() };
    }
    else {
        ex = uhe;
    }
}
```

而这个loopbackAddress翻译过来就是计算机网络中的回环地址，我们点进去

```java
public synchronized InetAddress loopbackAddress() {
    if (loopbackAddress == null) {
        byte[] loopback = {0x7f,0x00,0x00,0x01};
        loopbackAddress = new Inet4Address("localhost", loopback);
    }
    return loopbackAddress;
}
```

```java
byte[] loopback = {0x7f,0x00,0x00,0x01}
```

这个玩意转换成十进制就是127.0.0.1

那么我们直接在windows使用这个ip是访问不到wsl2的

## 解决

那么是不可能修改JDK源码的

也不知道wsl以后的更新会不会解决这个问题

目前一个的办法就是直接使用wsl2的内部ip地址：172.30.39.169
所以目前JAVA需要直接直接使用这个ip连接

但是这个ip一旦机器重启就会发生改变，我们的微服务项目又很多

只能采取一个折中的方案，定义一个host映射 local-->172.30.39.169