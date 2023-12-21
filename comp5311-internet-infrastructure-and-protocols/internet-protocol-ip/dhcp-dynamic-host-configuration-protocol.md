# DHCP（Dynamic Host Configuration Protocol）

## DHCP（Dynamic Host Configuration Protocol）

希望动态获得IP地址

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption><p>DHCP</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption><p>DHCP Scenario</p></figcaption></figure>

* 第一次broadcast，向服务器询问是否存在，还没指定地址，所以yiaddr是0.0.0.0
* 第二次服务器broadcst，返回一个可用第yiaddr，但是不知道地址是多少，所以给服务器自己的地址，其他broadcast
* 第三次可以broadcast，也可以直接给DHCP发，确认使用这个yiaddrr
* 第四次服务器broadcast，确认它使用这个地址，往后就可以通过地址直接发了。

