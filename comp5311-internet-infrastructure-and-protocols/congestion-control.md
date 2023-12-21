# Congestion Control

## Congestion

发的太多了，network不能承受了

* lost packets（buffer overflow at routers）
* long delays（queueing inrouter buffers）

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption><p>窗口需要大于上一个发的到上一个收到的</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption><p>发送速率等于窗口大小处以RTT</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

* TCP Reno版本，会将cwnd设置成一半，而TCPTahoe会设置成1
* ssthresh都设置为原来的一半

<figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption><p>Congestion Control State Machine Mechanism</p></figcaption></figure>

## TCP throughput（输出的速率 byte/sec）

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption><p>速率计算</p></figcaption></figure>

## TCP怎么保证Fairness的

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption><p>Scenario</p></figcaption></figure>

如果有两个TCP都连接到性能不行的路由器上，那么如何分配？

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption><p>Solution</p></figcaption></figure>

随机分配一个开始，然后增加，直到congestion。然后两个都会回到一半。那么多次之后，会越来越接近中间值，也就是equal bandwidth share。
