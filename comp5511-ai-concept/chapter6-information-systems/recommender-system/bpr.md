# BPR

先对样本负采样，再训练。通过刻画正负样本对区分情况，最大化区分能力来训练模型。

## Objective Function

$$
BPR\ Loss=\sum_{(u,i,j) \in O} {-\ln{\sigma(\hat y_{ui} - \hat y_{uj}) + \lambda {\Vert \Theta \Vert} ^2_2}}
$$

* 需要过sigmoid function
* 需要加上参数的l2正则化
