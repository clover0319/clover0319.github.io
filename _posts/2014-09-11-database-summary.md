---
layout: post
title: "数据库知识点"
description: ""
category: 数据库
tags: [数据库]
---
{% include JB/setup %}
# 数据库知识点
---


* **范式**

    所谓范式就是符合某一种级别的关系模式的集合。通过分解把属于低级范式的关系模式转换为几个属于高级范式的关系模式的集合。这一过程称为规范化。<br>
	1、 第一范式（1NF）：一个关系模式R的所有属性都是**不可分**的基本数据项。<br>
	那么符合第一模式的特点就有<br>
	1)有主关键字<br>
	2)主键不能为空，<br>
	3)主键不能重复,<br>
	4)字段不可以再分<br>
	2、 第二范式（2NF）：关系模式R属于第一范式，且**每个非主属性都完全函数依赖于键码**。<br>
	关系中每一个非主属性不部分依赖于主键<br>
	3、 第三范式（3NF）：关系模式R属于第一范式，且**每个非主属性都不传递依赖于键码**。<br>
	一般满足前三个范式就可以避免数据冗余。<br>
	4、 BC范式（BCNF）：关系模式R属于第一范式，且每个属性都不传递依赖于键码。即每个决定因素都包含码。<br>

* **事务具有哪些特性？ACID**

    原子性(Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）<br>
	(1) 原子性<br>
	事务的原子性指的是，事务中包含的程序作为数据库的逻辑工作单位，它所做的对数据修改操作**要么全部执行，要么完全不执行**。<br>
	(2) 一致性<br>
	事务的一致性指的是在一个事务执行之前和执行之后数据库都必须处于一致性状态。这种特性称为事务的一致性。假如数据库的状态满足所有的完整性约束，就说该**数据库是一致的**。<br>
	(3) 分离性(独立性)<br>
	分离性指并发的事务是**相互隔离**的。即一个事务内部的操作及正在操作的数据必须封锁起来，不被其它企图进行修改的事务看到。<br>
	分离性是DBMS针对并发事务间的冲突提供的安全保证。DBMS可以通过加锁在并发执行的事务间提供不同级别的分离。<br>
	(4)持久性<br>
	持久性意味着当系统或介质发生故障时，确保已提交事务的更新不能丢失。即一旦一个事务提交，DBMS保证它对数据库中**数据的改变应该是永久性的**，耐得住任何系统故障。持久性通过数据库备份和恢复来保证。<br>

* **SQL内连接与外连接用法与区别**
    数据表的连接有:<br>
	1、内连接(自然连接): 只有两个表相匹配的行才能在结果集中出现<br>
	2、外连接: 包括<br>
	（1）左外连接(左边的表不加限制)<br>
	（2）右外连接(右边的表不加限制)<br>
	（3）全外连接(左右两表都不加限制)<br>

* **存储过程和函数的区别**

	存储过程是用户定义的一系列SQL语句的集合，涉及到特定的表或其他对象的任务，用户可以调用。<br>
	函数通常是数据库已定义的方法，它接受参数并返回某种类型的值，并且不涉及特定用户表<br>






 

