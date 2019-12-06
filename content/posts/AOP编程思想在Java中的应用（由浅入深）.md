---
title: "AOP编程思想在Java中的应用（由浅入深）"
date: 2019-12-06T18:56:30+08:00
draft: true
---

## 写在前面
AOP，即**Aspect Oriented Programming（面向切面编程）**，相比于OOP（面向对象编程），AOP能够更好地对代码进行解耦，旨在将横切关注点与业务主体进行进一步分离，以提高程序代码的模块化程度。

## 从最基本的应用场景开始
假设一种情况，你有一个业务类`UserService`，其中有若干方法
```java
class UserService {
	
	public User getUserById(Integer Id) {
		return userDao.get(id);
	}
	
	public User insertUser(User user) {
		return userDao.insert(user);
	}
}
```
你希望在每个方法执行前打印方法开始的消息以及入参，那么最原始的办法就是，在方法的第一行嵌入打印语句（标准输出或日志），则上面的代码就变为：
```java
class UserService {
	
	public User getUserById(Integer id) {
		log.debug("getUserById invoked...");
		log.debug("param id: " + id);
		return userDao.get(id);
	}
	
	public User insertUser(User user) {
		log.debug("insertUser invoked...");
		log.debug("param user: " + user);
		return userDao.insert(user);
	}
}
```
这样看起来似乎也还OK，但是还不够优雅，毕竟修改了原先的代码。考虑一种情况，假如`UserService`来源于第三方依赖包，我们不能直接修改它的源码，但又

## Java中的AOP有哪些例子
- JDK动态代理
- CGLIB动态字节码增强
- Spring AOP

## JDK动态代理
```java
public static void main(String[] args) {
	System.out.println("asd");
}
```