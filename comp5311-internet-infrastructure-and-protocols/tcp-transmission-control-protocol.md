# TCP（Transmission Control Protocol）

* 点对点
* reliable， in-order byte stream
* pipelined（TCP拥堵（congestion）和流控制（flow control ，设置窗口大小））
* 全双工数据（full duplex data）
  * bi-directional data flow in same connection
* Maximum segment size（MSS，最大段大小）
  * 在数据交换前，handshaking 初始化sender和receiver的状态
*   流控制

    sender不会发爆receiver（overwhelm）

## Segment Structure

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption><p>TCP Segment Structure</p></figcaption></figure>

## Timeout

* 需要大于RTT（但是RTT是变化的）
* 过小的timeout会导致过早超时和不必要的重传
* 太长的timeout会导致对segment丢失响应过慢

## 如何设定Timeout

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption><p>Estimated RTT</p></figcaption></figure>

通过近期几个点，加权上一个estimatedRTT，得到新的预估RTT时间

\alpha通常是0.125

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

将RTT预估值和测量值的差也预测，那么timeout就是预估RTT加上四倍的预估差（因为预估差的系数是四分之一）

## Reliable Data Transfer

如果收到3个duplicated ACK是同一个包，那么下一个包可能丢失了。那就要重新传输

## Flow Control

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

需要在TCP Header中加入receive window（rwnd）大小，告诉发送方还有多少segment可用。

## Connect Management

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption><p>三次握手</p></figcaption></figure>

第一次发送syn，检测服务器是否存在

服务器收到syn，返回synack，就是告诉客户端收到了syn

第三次客户端收到了synack，发送ack和data

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption><p>四次挥手</p></figcaption></figure>

客户端发送FIN，服务器返回ACk

过一段时间，服务器发送FIN，确认客户端准备好哦，然后客户端返回ACK

