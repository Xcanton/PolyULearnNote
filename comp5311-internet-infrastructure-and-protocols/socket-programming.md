# Socket Programming

Socket是连接Application Process和实际End-end-transport protocol（TCP或UDP）的网络组成部分。

## Socket Programming with TCP

* Client必须和server连接
  * server必须在线
  * server必须对这个client创建socket
* Client和server连接时，需要
  * 创建本地的TCP socket
  * 指定服务器的IP地址和端口port号
  * 当client创建socket时，client发起TCP请求至服务器的TCP
* 当服务器收到客户端的TCP请求时，创建一个新的socket给服务器处理这个client的TCP通信
  * 可以同时通信多个客户
  * 多个端口可以加载不同的功能

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption><p>TCP客户端</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption><p>TCP服务端</p></figcaption></figure>

## "GET / HTTP/1.1\r\n\r\n"
