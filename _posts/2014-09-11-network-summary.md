---
layout: post
title: "计算机网络知识点"
description: ""
category: 计算机网络
tags: [计算机网络]
---
{% include JB/setup %}
# 计算机网络知识点
---



* **当你输入一个网址的时候，实际会发生什么?**

	[查看](http://www.cnblogs.com/wenanry/archive/2010/02/25/1673368.html)<br>
* **OSI参考模型**

	![Alt text](/image/OSI.png)

* **解释一下TCP/IP参考模型**

	TCP/IP参考模型分为四层：应用层（Application Layer）、传输层（Transport Layer）、网络层（Internet Layer）、链路层（Link Layer）。<br>
	TCP/IP分层&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;协议&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OSI 分层<br>
	应用层&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FTP,SMTP,Telnet,DNS,SNMP   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7<br>
	传输层                  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TCP,UDP                     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4<br>
	网络层            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IP, ICMP,(RIP, OSPF),ARP, RARP     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3<br>
	链路层     Ethernet,Token Bus,Token Ring,FDDI,WLAN  2,1<br>

* **TCP&&UDP**

	TCP（Transmission Control Protocol，传输控制协议）是基于连接的协议，也就是说，在正式收发数据前，必须和对方建立可靠的连接。<br>
	TCP一般用于传输大量数据、对可靠性要求高的应用环境，速度慢。<br>
	UDP（User Data Protocol，用户数据报协议）是与TCP相对应的协议。它是面向非连接的协议，它不与对方建立连接，而是直接就把数据包发送过去。 <br>
	UDP适用于一次只传送少量数据、对可靠性要求不高的应用环境，速度快。<br>

* **TCP为何采用三次握手来建立连接，若采用二次握手可以吗，请说明原因？**

	三次握手是为了防止已失效的连接请求再次传送到服务器端。<br>
	二次握手不可行，因为：如果由于网络不稳定，虽然客户端以前发送的连接请求以到达服务方，但服务方的同意连接的应答未能到达客户端。则客户方要重新发送连接请求，若采用二次握手，服务方收到重传的请求连接后，会以为是新的请求，就会发送同意连接报文，并新开进程提供服务，这样会造成服务方资源的无谓浪费。<br>
* **IP地址分类**

	简单的说，IP地址分5类，常见的地址是A、B、C类<br>
	A类<br>
	1.0.0.0 到126.0.0.0<br>
	0.0.0.0 和127.0.0.0保留<br>
	B<br>
	128.1.0.0到191.254.0.0<br>
	128.0.0.0和191.255.0.0保留<br>
	C<br>
	192.0.1.0 到223.255.254.0<br>
	192.0.0.0和223.255.255.0保留<br>
	D<br>
	224.0.0.0到239.255.255.255用于多点广播<br>
	E<br>
	240.0.0.0到255.255.255.254保留<br>
	255.255.255.255用于广播<br>




 


