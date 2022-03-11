---
layout: post
title:  "初探ThreadLocal"
date:   2019-05-10T11:59:33
category: JAVA
tags: [JAVA]
---

初探ThreadLocal

在使用spring boot的时候，发现这么样一个很有意思的功能：

```java
RequestContextHolder.getRequestAttributes()).getRequest()
```

可以通过这么样的一个类来获取当前的Request对象，第一反应就是spring boot替我们完成了request对象与当前线程的绑定。

那这内部，又是如何实现的？

![](https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1557413255826.png)

这个RequestContenxtHolder里面有一个ThreadLocal对象，这个对象，就是实现数据与线程绑定的核心对象。

那么ThreadLocal又是什么？

![](https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1557413403768.png)

从源码的注释大概可以了解到，这个类可以用来实现线程本地变量，我们来做个试验：

```java
public class Main{        
  private ThreadLocal<String> threadLocal = new ThreadLocal<>();
  public void set(String str){
    threadLocal.set(str);
  }
  public String get(){
    return threadLocal.get();
  }
  public static void main(String[] args) throws InterruptedException{
    Main main = new Main();
    main.set("hello");
    Thread thread = new Thread(()->main.set("world"));
    thread.start();
    thread.join();
    System.out.println(main.get());
  }
}
```

当运行这个程序的时候，会输出什么？

结果是hello，由于thread线程肯定是会在set("hello")之后，join()之前运行完毕的，所以我们可以从这个小例子当中初步了解ThreadLocal的用法。

那么我们知道，在JAVA内存模型当中，分为公共内存和线程私有内存，或者也叫工作内存。

线程私有内存是在栈上，那么我们能不能据此判断，ThreadLocal对象是在栈上？

继续看源码：

set方法：

```java
public void set(T value) {
  Thread t = Thread.currentThread();
  ThreadLocalMap map = getMap(t);
  if (map != null) {
    map.set(this, value);
  } else {
    createMap(t, value);
  }
}
```

get方法：

```java
public T get() {
  Thread t = Thread.currentThread();
  ThreadLocalMap map = getMap(t);
  if (map != null) {
    ThreadLocalMap.Entry e = map.getEntry(this);
    if (e != null) {
      @SuppressWarnings("unchecked")
      T result = (T)e.value;
      return result;
    }
  }
  return setInitialValue();
}
```

getMap方法：

```java
ThreadLocalMap getMap(Thread t) {
  return t.threadLocals;
}
```

从这三个方法来看，线程对象内部有一个ThreadLocal.ThreadLocalMap对象：

![](https://ismy1.oss-cn-qingdao.aliyuncs.com/blog/1557413873402.png)

正是通过这个map，才实现了线程与数据的绑定。