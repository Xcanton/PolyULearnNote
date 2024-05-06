# Deep Learning

深度学习和机器学习的本质区别体现在：

* 大多数的机器学习依赖于人工特征工程，构造越相关的高阶特征能够显著提升模型效果
* 深度学习可以从原始数据输入中自行学习到高阶特征的表示

## Learning Process

### 前向传播 Forward Propagation

* 将数据输入到神经网络中
* 隐层处理数据并通过激活函数，增加非线性拟合能力
* 输出层输出最终结果
* Weight
  * how important is that neuron
* Bias
  * allows for the shifting of \theta to the right or left

### 反向传播 Back Propagation

根据误差更新模型参数，减小误差的方向意味着提升模型性能。

## 激活函数 Activation Functions

激活函数的重要作用是：

*   增加网络的非线性能力

    Introduce non-linearity in the network
*   决定一个神经元是否可以对下层网络产生影响

    Decide whether a neuron can contribute to the next layer

激活函数的缺点有：（这个老师认为的）

* 分类问题中，希望确定一个输入是哪一类，但是却激活了很多个神经元。但其实最好的情况是只需要激活一个神经元，其他都为0。但是这种理想情况很难被拟合。（神经元不相互独立）
  * In a classification problem, if we want to predict which class one input belongs to, we will end up with multiple neurons activated.&#x20;
  * We want to have one neuron activated and others = 0. But it is difficult to converge.
* 最好的是神经元不是二元的，而是概率密度函数（实际上GeLUs、SwiGLU等新神经元已经能够实现）
  * Better if the activation is not binary and instead of some probabilities

### Sigmoid Function

<figure><img src="../.gitbook/assets/image (324).png" alt=""><figcaption></figcaption></figure>

### Tanh Function

<figure><img src="../.gitbook/assets/image (325).png" alt=""><figcaption></figcaption></figure>

有一个很有意思的事情是：tanh是sigmoid横纵都扩大一倍，然后向下平移1个单位的图像。

$$
2*sigmoid(2x) - 1 = \frac 2 {1+ e^{-2x}}-1 \\
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ = \frac {2-1-e^{-2x}} {1+e^{-2x}} \\
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ =\frac {1-e^{-2x}} {1+e^{-2x}} \\
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ =\frac {e^{x}-e^{-x}} {e^{x}+e^{-x}}
$$

### ReLU Function

<figure><img src="../.gitbook/assets/image (327).png" alt=""><figcaption></figcaption></figure>

取值为0时梯度不更新，Leaky ReLU解决这个Dying Gradient Problem

### Leaky ReLU（0.01x）

<figure><img src="../.gitbook/assets/image (328).png" alt=""><figcaption></figcaption></figure>

## Loss Functions

用来量化神经网络的输出与期望的输出的偏差

Quantify the deviation of the predicted output by the neural network to the expected output

* Regression: Squared Error, Huber Loss
* Binary Classification: Binary Cross-entropy, Hinge Loss
* Multi-Class Classification: Multi-Class Cross-Entropy, Kullback Divergence
