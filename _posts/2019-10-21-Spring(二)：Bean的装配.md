---
layout: post
title:  "Spring(二):Bean的装配"
date:   2019-10-21T09:00:00
category: Spring
tags: [Spring,Java]
---

讲解bean的装配

# 自动化装配

## 注解配置

当使用@Configutation注解的类，则声明该类为一个配置类，与配置类有关的注解还有：

- @ComponentScan
- @ComponentScans

它们都是用来指定包扫描路径的，使用方法如下：

```java
@Configuration
@ComponentScan("wang.ismy.spring")
public class Config {}
```

## 装配Bean

```java
@Component // 将当前类对象放入容器
public class Bean {...}
```

@Component这个注解修饰的类，如果类路径在容器的扫描路径中（兄弟包以及子包），则该类会被容器创建对象

与之作用相同的注解还有：

- @Controller
- @Service
- @Repository

这些注解只是语义不同，作用都是一样的。

## 使用Bean

要使用这个Bean，我们首先需要创建一个容器：

```java
AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(Config.class);
```

然后，我们可以从中获取Pojo这个类型的对象：

```java
context.getBean(Pojo.class)
```

不仅可以使用Bean的类型获取Bean，也可以使用Bean的名称获取：

```java
context.getBean("pojo");
```

## 生命周期方法

有时候，我们需要Bean在创建后或者销毁前做一些事情：我们可以使用以下两个注解来实现：

```java
    //创建后执行
    @PostConstruct
    public void init(){ System.out.println("init"); }

    //销毁前执行
    @PreDestroy
    public void destroy(){ System.out.println("destroy"); }
```

需要注意的是，这两个注解都不是Spring提供的，它是JAVA EE的标准，在使用的时候需要添加相关依赖

```xml
        <dependency>
            <groupId>javax.annotation</groupId>
            <artifactId>javax.annotation-api</artifactId>
            <version>1.3.2</version>
        </dependency>
```

## 自动注入

Spring提供了一个最核心的功能就是依赖注入，也就说，Spring帮我们处理了各个对象之间的依赖关系，当一个对象创建时，Spring会找到这个对象所需要的依赖进行注入，我们只需要在要进行依赖注入的地方做一个标记即可，这个标记就是@Autowired

```java
@Component
public class Bean {

    private Bean1 bean1;

    @Autowired
    public Bean(Bean1 bean1) {
        this.bean1 = bean1;
    }

    public void say(){
        System.out.println("hi");
        bean1.run();
    }
}
```

这个注解不仅能加在构造函数上，也能放在成员变量、setter方法。
不过如果Bean只有一个构造函数，则可以省略这个注解。

## JAVA代码注入

由于某些类来源于外部，我们无法修改其源码 所以可以使用java代码的方式创建后注入

```java
@Configuration
public class Config {
    @Bean
    public Bean1 bean1(){return new Bean1();}
}
```

## 处理自动装配歧义性

在使用容器的时候，难免会遇到需要同类不同实例的对象，那么这时候又该怎么办？

解决方法有两个：

- 从生产方解决
- 从消费方解决

```java
@Bean
@Primary // 标示首选bean
public Bean1 bean1(){
    Bean1 bean1 = new Bean1();
    bean1.setName("pro");
    return bean1;
}
```

```java
@Autowired
@Qualifier("bean1f") // 当有多个可选项时，将使用名为bean1f的bean
public void setBean1(Bean1 bean1){}
```

## Bean的作用域

- singleton：单例，即在整个容器中只会有一个同类型对象
- prototype：每次获取都会创建实例
- session：每个会话一个bean（此处的会话指web容器的会话Session）
- request：每个请求一个bean（web容器的Request）
- global session：应用在Portlet环境.如果没有Portlet环境那么globalSession相当于session

## 条件装配

可能我们的Bean并不是每次都需要创建，那么则可以使用条件化装配

```java
@Bean
@Conditional(MyConditional.class)
public Bean1 bean1(){
    Bean1 bean1 = new Bean1();
    bean1.setName("pro");
    return bean1;
}
```

只要实现Condition接口，就可以控制Bean的创建与否

```java
  public class MyConditional implements Condition {

    @Override
    public boolean matches(ConditionContext context, AnnotatedTypeMetadata metadata) {

        return true;
    }
  }
```

## 运行时值注入

在运行时，我们可能需要外部配置文件的一些值，我们可以先通过配置类注入配置文件

```java
@Configuration
@ComponentScan(basePackages = "wang.ismy.spring")
@PropertySource("classpath:config.properties")
public class Config { }
```

在Bean中，可以使用@Value注解注入值

```java
@Component
public class Bean {
  @Value("${name}")
  String name;
}
```

### SPEL


Spring Expression Language（Spring表达式），是一种类似于脚本语言的东西，我们可以通过在@Value中写一些字符串以此来达到语言级的能力：

```java
@Value("#{T(System).currentTimeMillis()}") // 获取当前时间
long time;
```

## 导入配置

使用@Import可导入其他配置类

```java
@Configuration
@Import({DevConfig.class,ProConfig.class})
public class MasterConfig { }
```

## 配置环境

在开发与测试或者生产环境，很多配置都是不一样的，如果需要频繁地改，那会是很麻烦的，我们可以为配置指定一个环境，在不同的场景启用不同的环境

```java
@Configuration
@Profile(("dev")) // 开发环境配置
public class DevConfig {}
```

```java
@Configuration
@Profile("pro") // 生产环境配置
public class ProConfig {}
```

我们需要一个主配置，导入所有的配置：

```java
@Configuration
@Import({DevConfig.class,ProConfig.class})
public class MasterConfig { }
```

在使用注解上下文时，我们使用这个主配置为引导类

### 激活

方法有两种，一是设置环境变量，二是手动编码

```java
System.setProperty("spring.profiles.active","dev"); // 通过设置环境变量
```

```java
// 手动编码设置
AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext();
context.getEnvironment().setActiveProfiles("dev");
context.register(MasterConfig.class);
context.refresh();
```


