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

## Optimizers

During training, we adjust the parameters to minimize the loss function and make our model as optimized as possible

Tie together the loss function and model parameters by updating the network based on the output of the loss function

Loss function guide optimizers (我们像神经网络，降序的方向是缩小的误差， loss function是我们的脚)

### 梯度下降 Gradient Descent

梯度下降是最古早的optimizer之一，它从初始化的节点开始，并且迭代至损失函数的最低点。

Gradient Descent - the granddaddy of optimizers. The iterative algorithm starts off at a random point on the loss function and travels down its slop in steps until reach the lowest point of the function.&#x20;

<figure><img src="../.gitbook/assets/image (329).png" alt=""><figcaption></figcaption></figure>

梯度下降的特点是：

* Most Popular Optimizer
* Fast、Robust、Flexible

梯度下降的算法步骤是：

1.  计算当前模型和期望输出的差值

    Calculate what a small change in each individual weight would do to the loss function
2.  根据梯度调整参数

    Adjust each parameter based on its gradient
3.  重复第一第二步直至最低点

    Repeat 1 and 2 until the loss function is as low as possible

<mark style="color:red;">优点</mark>：

*   梯度下降对多数情况都适合

    Gradient descent works best for most purposes

<mark style="color:red;">缺点</mark>：

1.  数据集大的时候计算昂贵

    Expensive to calculate the gradients if the size of the data is huge
2.  对于非凸函数不能保证求解

    Gradient descent works well for convex functions, but it does not know how far to travel along the gradient for nonconvex functions

### 随机梯度下降 Stochastic Gradient Descent

随机梯度下降和梯度下降类似，不同的是它采用batches（也就是训练样本的子集来更新数据）。

随机梯度下降用动量（<mark style="color:red;">Momentum</mark>）来累计梯度，累计的梯度决定下一个step的参数更新和模型训练走向。

Uses momentum to accumulate gradients. Accumulate gradient in the past to dictate what might happen in the next step.

随机梯度下降的好处有：<mark style="color:red;">计算强度较低（Less intensive computationally）</mark>

随之而来的不足是：<mark style="color:red;">数据子集会导致抽样噪声，需要更大的训练轮数来收敛。</mark>（Not using the whole dataset -> noise -> higher iteration to reach the local minima）

<mark style="color:red;">坏处</mark>：

*   增加的训练轮次导致总训练时长增加

    Overall computation time increases due to an increase in the number of iterations

### Adagrad（<mark style="color:green;">Ada</mark>ptive <mark style="color:green;">Gra</mark>dient <mark style="color:green;">D</mark>escent）

*   根据输入的样本调整学习率

    Adapts learning rate to individual features
*   部分权重有自身独特的学习率

    Some weights will have different learning rates
*   <mark style="color:red;">非常适合部分特征缺失的稀疏数据集</mark>

    Ideal for <mark style="color:red;">Sparse datasets with many input examples missing</mark>
*   学习率逐渐减小

    LR tends to get small with time

<mark style="color:red;">好处</mark>：

1.  对离散的特征和稠密特征都适用

    Adagrad works well with real-world datasets that contain sparse as well as dense features
2.  能够对不同的特征实现不同的学习率，每个特征都能够被快速收敛

    Assign different learning rates for different features. Reaches convergence at a higher speed

<mark style="color:red;">坏处</mark>：

1.  它的学习率下降很快

    It decreases the learning rate aggressively and monotonically
2.  在小学习率时，模型并不能持续获得新的知识，限制了模型准确性

    Due to small learning rates, the model eventually becomes unable to acquire more knowledge, the accuracy of the model is compromised.

### RMSprop（<mark style="color:red;">R</mark>oot <mark style="color:red;">M</mark>ean <mark style="color:red;">S</mark>quare <mark style="color:red;">Prop</mark>agation）

*   减少了动量导致的学习率下降

    Reduces the monotonically decreasing learning rate
*   在一个固定长度的窗口中累计梯度

    Accumulates gradients in a fixed window
*   主要聚焦在优化器的加速上

    Mainly focuses on accelerating the optimization process

    *   通过减少优化函数执行次数

        By decreasing the number of function evaluations to reach the local minima
*   损失函数有振荡

    Update parameters that oscillate cost function

<mark style="color:red;">好处</mark>：

*   RMSProp能够快速收敛，并且不需要太多调整

    RMSProp converges quickly and requires less tuning

<mark style="color:red;">坏处</mark>：

*   需要手动设定学习率，并且适用的学习率会根据任务不同变化

    The learning rate has to be defined manually and the suggested value does not work for every application

### Adam（<mark style="color:red;">Ada</mark>ptive <mark style="color:red;">M</mark>oment Estimation）

*   是随机梯度下降的优化版本

    Extension of stochastic gradient descent. Update network weights during training
* 采用动量的概念

<mark style="color:red;">好处</mark>：

1.  性能出色，是深度学习常用的默认的优化器

    a benchmark for DL papers and recommended as a default optimization algorithm
2.  易于实施

    Straightforward to implement
3.  运行速度快

    Fast running time
4.  内存占用少

    Low memory requirements
5.  比其他优化器需要设定的参数都少

    Less tuning than any other optimizers

<mark style="color:red;">坏处</mark>：

1.  更关注快速计算，而不是对数据点的拟合效果

    focus on faster computation time, whereas other algorithms focus on data points
2.  所以导致部分时候模型效果不如SGD

    That's why algorithms like SGD generalize the data in a better manner at the cost of low computation speed

## Overfitting

### Dropout、Augmentation、Early Stopping

## Neural Network Architectures

* inputs
* Outputs
* hidden layers
* neurons per hidden layer
* Activation functions

### Feed Forward Neural Networks

* Take in fixed-sized inputs
* Returns fixed-sized inputs
* Information about the past is not applied
* Vanilla neural networks can not handle sequential data

### Recurrent Neural networks

* Uses a feedback loop in the hidden layers
* Predict letters based on previously-typed letters
* all letters typed are equally important in the prediction

#### Vanishing Gradient Problem

由于RNN层数与输入序列长度有关，长输入序列会导致梯度小时或者梯度爆炸。

#### LSTM

#### Gated RNN（GRNN）

#### 好处

1.  可以处理不定长序列

    Can handle input of any length
2.  可以从过去的信息中过去数据

    You can trace the information of the previous time steps
3.  模型的参数相对固定，不随着样本序列增长

    The model parameters are fixed in size, independent of the input length

#### 坏处

1.  计算时间贼久

    Long calculation time
2.  长周期捕捉能力差

    It is difficult to trace the information of a long time step

### Convolutional NNs

* Inspired by the organization of neurons in the visual cortex of the human brain
* Good for processing data like images, audio and video
* Convolutional layers
* Pooling layers
* Fully-connected layers
* Normalization layers

### Language Modeling

<figure><img src="../.gitbook/assets/image (330).png" alt=""><figcaption></figcaption></figure>

#### N-Gram Model

[n-grams](../comp5423-natural-language-processing/n-gram-language-models/n-grams/ "mention")

