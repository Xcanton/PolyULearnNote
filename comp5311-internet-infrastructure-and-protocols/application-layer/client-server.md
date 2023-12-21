# Client-Server

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption><p>Client-Server Architecture</p></figcaption></figure>

## Server

* 永远在线（always-on host）
* 固定的IP地址
* 可以通过内部集群扩张提升性能（server farms for scaling）

## Clients

* 与server通信
* 可能会间歇性连接（intermittently connected）
* 可能有变化的IP地址
* 不直接与其他Client通信
