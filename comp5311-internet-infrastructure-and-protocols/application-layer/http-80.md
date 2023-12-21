# HTTP（80）

## HTTP（Hypertext Transfer Protocol）

Web's application layer protocol

* 客户端发起到服务器的TCP连接（端口port 80）
* 服务器接收来自客户端的TCP连接请求
* HTTP消息在浏览器和Web服务器之间传递
* TCP连接中断

### HTTP is stateless

服务器不维护有关过去客户端的请求

### HTTP/1.0 （Nonpersistent HTTP）

所有的object都在一个TCP请求里发送

### HTTP/1.1（Persistent HTTP）

可以通过客户端和服务器的单个TCP连接发送多个对象

## Response Time Modeling（RTT）

time to send a small packet to travel from client to server and back

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

### Response time

* 需要一个RTT初始化TCP连接
* 一个RTT提供HTTP请求和第一个HTTP返回少量的数据

所以一共需要2RTT+transmit time

### Nonpersistent HTTP issues

* 每个对象需要两个RTT
* 操作系统必须为每个TCP连接分配主机资源
* 浏览器经常打开并行TCP连接来获取引用的对象

### Persistent HTTP

* 浏览器在发送响应以后保持连接打开
* 同一客户端/服务器之间的后续HTTP消息通过连接发送

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption><p>HTTP Request Message</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption><p>HTTP Response Message</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>手动发送GET请求</p></figcaption></figure>

## Cache

### Goal

Satisfy client request without involving origin server

## Why

* Reduce response time for client request
* Reduce traffic on an institution's access link
* poor content providers to effectively deliver content
