# NAT（Network Address Translation）

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption><p>NAT</p></figcaption></figure>

为了扩展ip的可用数量，所以将内部设置为另一个translation

可以更换ISP外部网络，不用更换内部网络结构

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption><p>Scenario</p></figcaption></figure>

通过port端口号不同在NAT Translation Table上注册不同子网络的地址，并且在转发请求的时候，将source id更换成路由器自己的ip和端口号（16bit）

* 不应该超过三层，因为每个机器可以多端口开，那么如果层数多，最外层会很快消耗完端口号
* 违背了端到端协议（end-to-end argument）
* 缺陷应该在IPv6中解决

## 三种连接方式

### 静态注册服务器在router上

### 动态注册

### Proxy（通过代理服务器，客户端只连接代理服务器）

