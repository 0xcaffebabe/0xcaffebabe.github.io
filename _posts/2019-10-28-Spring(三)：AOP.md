---
layout: post
title:  "Spring(三):AOP"
date:   2019-10-21T09:00:00
category: Spring
tags: [Spring,Java]
---

讲解Spring的Aop

# AOP

## 什么是AOP

>百度百科：在软件业，AOP为Aspect Oriented Programming的缩写，意为：面向切面编程，通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。

## 实现原理

在JAVA中，AOP使用动态代理实现，而动态代理实现方式分为两种：

- 以JDK动态代理为代表的基于接口的动态代理
- 以CGLIB为代表的基于父类的动态代理

更多关于AOP的内容可以参考之前的文章:

- [谈谈AOP](https://ismy.wang/java/2018/08/19/%E8%B0%88%E8%B0%88AOP.html)
- [探秘AOP实现原理](https://ismy.wang/java/2018/08/24/%E6%8E%A2%E7%A7%98AOP%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86.html)

## AOP的作用

![enter image description here](https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=764221332,501156740&fm=26&gp=0.jpg)

## AOP术语

- 通知(Advice):所谓通知是指拦截到Joinpoint之后所要做的事情就是通知

  - 前置通知（before）:执行前执行
  - 后置通知（after）：执行后执行
  - 返回通知（after returning）
  - 异常通知（after throwing）
  - 环绕通知（around）

_使用xml时，后置通知与返回通知以及异常通知的执行顺序取决于配置顺序_

- 连接点(Joinpoint):所谓连接点是指那些被拦截到的点。在spring中,这些点指的是方法,因为spring只支持方法类型的连接点。
- 切点(Pointcut):所谓切入点是指我们要对哪些Joinpoint进行拦截的定义。
- 切面(Aspect):是切入点和通知（引介）的结合。
- 引入(Introduction):引介是一种特殊的通知在不修改类代码的前提下, Introduction可以在运行期为类动态地添加一些方法或Field。
- 织入(Weaving):是指把增强应用到目标对象来创建新的代理对象的过程。

## 使用AOP

使用AOP之前，我们需要引入相关的依赖：

```xml
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aop</artifactId>
            <version>5.2.0.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjweaver</artifactId>
            <version>1.9.4</version>
        </dependency>
```

并且要在配置中开启
```java
@EnableAspectJAutoProxy
```

```java
@Aspect
@Component //定义一个切面组件，注入给Spring容器管理
public class MyAspect {

    // 定义一个切点
    @Pointcut("execution(* wang.ismy.spring.Bean.run())")
    public void point(){}

    // 使用该节点编写前置通知
    @Before("point()")
    public void before(JoinPoint joinPoint){
        System.out.println(joinPoint.getSignature().getName());
    }
}
```

这样，当Bean执行run方法之前，它总是会调用before方法。

切点不仅能使用execution编写，而且还能用如下方法编写：

![](https://img2018.cnblogs.com/blog/475392/201810/475392-20181031104431559-1365885037.png)

详情请参考Spring文档: [5.2.0文档](https://docs.spring.io/spring/docs/5.2.0.RELEASE/spring-framework-reference/core.html#aop-api)

# 总结

AOP是建立在DI上的一个重要功能，Spring的很多重要功能譬如事务管理都是建立在AOP上的，理解AOP及其原理能更好地使用Spring框架。


