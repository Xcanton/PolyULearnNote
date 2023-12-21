# DNS

## Domain Name System

*   distributed database

    多层结构的许多名称服务器
*   application- layer protocol

    host、routers、服务器

    resolve names
* 是核心的网络功能，实现在应用层协议

Client wants IP for www.amazon.com; 1st approx:

* Client queries a root server to find com DNS server
* Client queries com DNS server to get amazon.com DNS server
* Client queries amazon.com DNS server to get  IP address for www.amazon.com
*

## Top-level Domain（TLD） Server

负责com、org、net、edu和所有顶层多家domain（uk、fr、ca、jp）

## Authoritative DNS servers

组织性质的DNS服务器，为主旨的服务器提供权威主机名到IP的映射

可由主治或服务提供商维护

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption><p>Local Name Server</p></figcaption></figure>

## Local Name Server

严格意义上不属于DNS服务器层级，每个ISP（住户ISP、公司、大学）都可以拥有一台本地名称服务器

Also called "default name server"

当主机发出DNs查询时，查询将发送到本地DNS服务器，充当代理，并将查询转发到层次结构中

* Recursive Query（一条线访问）
* Iterated Query（不知道就返回可能的服务器，让user自己去下一个找）

