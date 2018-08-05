## Spring Core Technologies

### 官方文档，英语单词释义

```
reference: 参考
integral: 必须的，不可或缺的
inversion: 反转
inversion of Control (IoC): 控制反转
foremost: 最重要的
amongst: 在什么之中
comprehensive: 全面的
conceptually: 概念的
integration: 集成
principle:原理
within: 在什么之内
that is: 也就是说
work with: 与什么共事
hence: 因此
easier: 更简单
```
### IoC 容器
#### 介绍 Spring IoC 容器和实体对象(beans)
这节涵盖了Spring Framework IoC（控制反转） 实现的原理。IoC 也叫依赖注入。这个过程通过对象定义它们的依赖关系，也就是说它们使用的其他对象，仅仅能通过构造函数参数，工厂方法参数，或在构造或工厂方法返回的对象上设置属性。当容器创建 beans 的时候注入这些依赖项。这个过程从根本上是相反的，因此它的名字叫控制反转(IoC)，bean 本身通过使用类的直接构造或诸如 Service Locator 模式之类的机制来控制其依赖关系的实例化或位置。

包 org.springframework.beans 和 org.springframework.context 是 Spring Framework 容器的基础。BeanFactory 接口提供了一种能够管理任何类型对象的高级配置机制。ApplicationContext 是 BeanFactory 的子接口。它增加了与Spring Aop 功能的简单集成。消息资源处理(用于国际化)，事件发布，和特定应用程序的 Context，例如，WebApplicationContext 用于 web 应用程序。

简单说，beanFactory 提供配置框架的基本功能，ApplicationContext 添加了很多 企业级特定功能，ApplicationContext 是 BeanFactory 的完整的超集。

在 Spring 中，bean 构成了应用程序的主干，并通过 Spring 容器，初始化，组装和管理。在应用程序中通过很多的 bean 组成，它们直接的依赖关系反应在容器使用的配置的元数据中。

#### Container overview

这个接口 org.springframework.context.ApplicationContext 表明 Spring IoC 容器是负责 初始化，配置和组装这些 beans。这个容器通过读取配置的元数据来获取 初始化，配置和组装的指令。这个配置的元数据以 XML，Java 注解 或者 Java code。它允许你表达组成应用程序的对象以及这些对象之间丰富的相互依赖性。

ApplicationContext 几个接口的实现在 Spring 中开箱即用。在独立的应用程序中，通常会去创建 ClassPathXmlApplicationContext 或 FileSystemXmlApplicationContext 的实例。

#### Configuration metadata

