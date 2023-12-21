# Reliable Data Transfer（RDT）

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption><p>Reliable Data Transfer</p></figcaption></figure>

用有限状态机（finite state machine， FSM）来制定sender和receiver

## RDT 1.0

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption><p>RDT 1.0</p></figcaption></figure>

假设channel是完全可信的

* 没有bit error和packet loss
* 发送方塞入channel，接收方取出

## RDT 2.0（加入checksum）

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption><p>RDT 2.0</p></figcaption></figure>

通过checksum记录一个包里面的bit的和（2，3，5，额外发送10）

### How to recover？

从新发送，引入机制feedback，返回ACKs或者NAKs（比RDT 1.0新加的，另一个新加的是 Error Detection）

### 问题

如果ack和nak是坏的，那么会导致重发或者漏发

## RDT 2.1（加入sequence number）

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption><p>RDT 2.1 Sender</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption><p>RDT 2.1 Receiver</p></figcaption></figure>

## RDT 2.2 （NAK-free）

发送ack+最后一个ack的包id（ack2意味着package3坏了）

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption><p>RDT 2.2</p></figcaption></figure>

## RDT 3.0（加入timeout，reasonable amount of time）

假设channel还有packet loss（上面只考虑bit error的情况了）

如果没有ack返回，那就重发。

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption><p>RDT 3.0</p></figcaption></figure>

## Performance

### RDT 3.0 性能很烂

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption><p>RDT 3.0 transfer time</p></figcaption></figure>

所以需要引入pipeline protocols（允许几个包一起传，等待ack）

* Go-Back-N（发送pipeline中最多有N个）
  * receiver只发送连续的（cumulative）ack，如果有gap那就不累计
  * sender有个timer，对最老的还没ack对包 如果过久没ack那就从这重发
* Selective Repeat
  * 不同的是 发送individual ack
  * 0123，window size3 会导致要是0重发，就不知道是第0个还是第4个



