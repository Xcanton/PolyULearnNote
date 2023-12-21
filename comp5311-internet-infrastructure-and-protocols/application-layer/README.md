# Application Layer

## Network application的好处

* 在不同的end system上运行
* 在网络中通信
* 网络的核心组成设备不需要额外更改，所以支持快速的app开发

## 不同的网络架构

[client-server.md](client-server.md "mention")[peer-to-peer.md](peer-to-peer.md "mention")[hybrid-of-client-server-and-p2p.md](hybrid-of-client-server-and-p2p.md "mention")

## 如何process communicating

### Process的定义

program running within a host

* 在同一个host中，两个进程通过进程间通信（inter-process communication）与其他进程交互（操作系统提供）
* 在不同的host中，进程通过交换信息（exchanging messages）通信

### 不同host在通信中扮演不同的角色

#### Client Process

向服务器发起通信

#### Server Process

等待客户端连接

#### P2P既有client process又有server process

### Sockets

* 实际处理收发信息的机制
* 类似于邮政系统
* API
  * 选择对应的传输协议
  * ability to fix a few parameters

## What transport service does an app need?

* Data Loss
  * 有些app可以接受丢失
  * 例如文件传输、远程登陆需要100%可靠的数据传输
* Timing（时效性）
  * 例如网络电话（Internet telephony）和实时交互的游戏需要低延迟（effective）
* Bandwidth
  * 有些app（multimedia）只需要一个最低限度的带宽才能正常使用
  * 其他app（elastic apps）你给它啥带宽他就将就着用

[tcp-and-udp-protocols.md](tcp-and-udp-protocols.md "mention")

## What are Applications and App-Layer Protocols

HTTP

* 是超文本传输协议（HyperText Transfer Protocol）
* 是万维网使用的底层协议（the underlying protocol used by the World Wide Web）
* 定义了信息的格式化和传输方式，以及Web服务器和浏览器应采用哪些操作来响应各种命令
* 万维网的另一个标准是HTML，它涵盖了网页是如何formatted和展示的

[http-80.md](http-80.md "mention")
