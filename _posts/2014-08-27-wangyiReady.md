---
layout: post
title: "网易面试准备"
description: ""
category: 面试准备
tags: [面试准备]
---
{% include JB/setup %}
# 网易面试准备
---



1. 抽象类和接口 <br>
一个类可以有多个接口 只能有继承一个父类<br>
抽象类可以有构造方法  <--> 接口中不能有构造方法。<br>
抽象类中可以包含静态方法  <--> 接口中不能包含静态方法 <br>
抽象类中可以有普通成员变量 <--> 接口中没有普通成员变量<br>
抽象类的可以有实现了的方法 <--> 接口里边全部方法都必须是abstract的<br>
抽象类中的抽象方法的访问类型可以是public，protected 
<--> 接口中的抽象方法只能是public类型的，并且默认即为public abstract类型<br>
抽象类和接口中都可以包含静态成员变量:<br>
抽象类中的静态成员变量的访问类型可以任意 <--> 接口中定义的变量只能是public static final类型，并且默认即为public static final类型。
<!--break-->
2. Java 反射机制 <br>
JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。<br>
Java反射机制主要提供了以下功能： 在运行时判断任意一个对象所属的类；在运行时构造任意一个类的对象；在运行时判断任意一个类所具有的成员变量和方法；在运行时调用任意一个对象的方法；生成动态代理。

3. Java 多态<br>
运行时多态性是面向对象程序设计代码重用的一个最强大机制，Java多态性的概念也可以被说成“一个接口，多个方法”。<br>
Java实现运行时多态性的基础是动态方法调度，它是一种在运行时而不是在编译期调用重载方法的机制。<br>
方法的重写Overriding和重载Overloading是Java多态性的不同表现。重写Overriding是父类与子类之间多态性的一种表现，重载Overloading是一个类中多态性的一种表现。<br>

4. Java 实现多线程<br>
在java中要想实现多线程，有两种手段，一种是继续Thread类，另外一种是实现Runable接口。<br>
实现Runnable接口比继承Thread类所具有的优势：<br>
1）适合多个相同的程序代码的线程去处理同一个资源<br>
如果一个类继承Thread，则不适合资源共享。但是如果实现了Runable接口的话，则很容易的实现资源共享。<br>
2）可以避免java中的单继承的限制<br>
3）增加程序的健壮性，代码可以被多个线程共享，代码和数据独立。<br>

5. String StringBuffer StringBuilder 的区别<br>
String 字符串常量，不可变<br>
StringBuffer 字符串变量，线程安全<br>
StringBuilder 字符串变量，线程不安全，单线程中使用<br>

6. Session和cookie<br>
Cookie通过在客户端记录信息确定用户身份，Session通过在服务器端记录信息确定用户身份。<br>
Web应用程序是使用HTTP协议传输数据的。HTTP协议是无状态的协议。一旦数据交换完毕，客户端与服务器端的连接就会关闭，再次交换数据需要建立新的连接。这就意味着服务器无法从连接上跟踪会话。Cookie就是这样的一种机制。它可以弥补HTTP协议无状态的不足。<br>
Session是另一种记录客户状态的机制，不同的是Cookie保存在客户端浏览器中，而Session保存在服务器上。客户端浏览器访问服务器的时候，服务器把客户端信息以某种形式记录在服务器上。这就是Session。客户端浏览器再次访问时只需要从该Session中查找该客户的状态就可以了。<br>
如果说Cookie机制是通过检查客户身上的“通行证”来确定客户身份的话，那么Session机制就是通过检查服务器上的“客户明细表”来确认客户身份。Session相当于程序在服务器上建立的一份客户档案，客户来访的时候只需要查询客户档案表就可以了。<br>

7. Servlet的生命周期<br>
初始化阶段  调用init()方法<br>
响应客户请求阶段　　调用service()方法(doGet&&doPost)<br>
终止阶段　　调用destroy()方法<br>
一个实例可以服务于多个请求，并且其实例一般不会销毁。<br>

8. Statement和preparedStatement<br>
应该始终以PreparedStatement代替Statement，原因是：<br>
代码的可读性和可维护性<br>
PreparedStatement尽最大可能提高性能：每一种数据库都会尽最大努力对预编译语句提供最大的性能优化<br>
极大地提高了安全性，防止SQL注入（or 1=1）<br>

9. Redirect 和 forward<br>
Redirect：URL重新定向，可以是任意的URL； 不能共享request里面的数据 ；一般用于用户注销登录时返回主页面和跳转到其它的网站等等<br>
Forward：页面的转发，只能是同一个Web应用程序的其他Web组件；转发页面和转发到的页面可以共享request里面的数据；一般用于用户登录的时候根据角色转发到相应的模块等等。<br>

10. Java 内存模型<br>

11. JVM垃圾回收实现原理<br>
 


