# FTP（control21,data20）

* 通过21端口连接FTP服务器，指定TCP作为传输协议
* 客户端获得控制连接授权
* 客户端通过控制连接发送命令来浏览远程目录
* 当服务器接收到文件传输命令时，服务器打开与客户端的TCP数据连接
* 传输一个文件后，服务器关闭连接

三个major Components

* User Agents
* Mail Servers
* Simple mail transfer protocol： SMTP

User Agent（mail reader，类似于Outlook）

* 编写（composing）、编辑和阅读邮件消息
* 传出（outgoing）和传入（incoming）消息都保存在服务器上。

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

Mail Server

* mailbox包含传入的用户消息
* message queue包含待发送的邮件消息
  * 客户端：发送邮件的服务器
  * 服务器：接收邮件的服务器

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption><p>Scenario</p></figcaption></figure>

## Message Access Protocols

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

SMTP负责传输和保存到收件人的邮箱服务器

Mail access protocol 是负责从自己的邮箱服务器收邮件

* [pop.md](pop.md "mention")
* [imap.md](imap.md "mention")
* [http-80.md](../application-layer/http-80.md "mention")Hotmail, Yahoo
