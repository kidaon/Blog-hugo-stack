---
title: MVC与解耦
date: 2025-02-28
categories: 
    - 学习笔记
    - Maven
    - SpringBoot
tags:
    - MVC框架
    - IOC
    - DI
---

## MVC 架构模式

### 基本概念
**MVC（Model-View-Controller）** 是一种分层架构设计模式：
- **Model（模型）**：数据层，处理业务逻辑和数据持久化
- **View（视图）**：展示层，负责用户界面呈现
- **Controller（控制器）**：协调层，处理用户输入并调用模型/视图
### 目录结构
下面是我创建的一个应用MVC架构的建议框架
{{< figure src="1.png" width="400" >}}
- pojo用于存放普通Java对象，包括属性值和对应的getters和setters。类似的还有DAO（view），一般是数据库中实体表的映射，就像视图一样。
- service是对pojo的再次封装，封装成一个方法，例如要对pojo中的其中一个类做什么操作，或者是对DAO中的类做数据库的增删改查操作，就写在对应的service中。
- Controller负责请求转发，用于接受和返回前端页面的参数，一般会调用service中的不同方法。
### 工作流程
1. 用户在浏览器输入 URL 或点击按钮，发送 HTTP 请求。
2. 请求被 DispatcherServlet（Spring MVC 的核心）拦截，并匹配对应的 Controller。
3. Controller 处理请求，调用 Service 层执行业务逻辑。
4. Service 层可能会调用 DAO 层访问数据库，并返回数据。
5. Controller 获取数据后，返回 JSON 响应或视图模板（前后端不分离时）。
6. View 层将数据渲染，并呈现给用户。

## IOC与DI

IOC（Inversion of Control，控制反转）是一种设计思想，主要目的是将对象的创建和依赖管理交给 Spring 容器，而不是在代码中手动创建对象。而DI（Dependency Injection，依赖注入）是 IOC 的实现方式。它用于自动注入对象，避免手动创建依赖对象，提高可维护性。
### IOC
- **传统方式**
```java
UserService userService = new UserServiceImpl();
```
由调用者负责创建 UserService 实例,是强耦合，不利于管理和扩展。

- **IOC 方式**
```java
@Component
public class UserServiceImpl implements UserService {
    // 业务逻辑
}
```
通过 @Component 将 UserServiceImpl 交给 IOC 容器，使其被 Spring 容器管理，无需手动创建通过，降低了耦合。
### DI
常见的依赖注入方式主要有三种：
1. 构造方法注入
```java
@Service
public class UserService {
    private final UserRepository userRepository;
    
    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```
2. Setter 方法注入
```java
@Service
public class UserService {
    private final UserRepository userRepository;
    
    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```
3. 字段注入
```java
@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;
}
```
其中字段注入最为简洁，但构造方法注入的可维护性更高（更推荐）。
### 总结
简单来说，就是``@Component ``将当前类交给IOC容器存储，``@Autowiredzai``在应用程序运行时，会自动的査询该类型的bean对象,并赋值给该成员变量。通过接口->IOC->DI->调用，实现了解耦。