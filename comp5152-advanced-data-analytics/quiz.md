# Quiz

## Quiz 1

### What can we learn if we visualize our dataset into histograms?

**直方图能看出什么**

1. Distribution of your dataset 数据分布
2. ~~The size of the data~~
3. The presence of outliers 是否有异常值
4. Most frequent events/items 最频繁项

### Select all the unstructured data from the following options

**判断是否是结构化数据**

1. News article 新闻报道
2. Forum posts 论坛帖子
3. ~~SQL database~~&#x20;
4. ~~Computer system log file~~

### We can calculate the mean value for nominal scale data and achieve meaningful results

**适量数据的均值是不是有意义的结果**

1. ~~True~~
2. False 不是

### Choose the correct statements about hypothesis testing

**以下关于假设检验正确的是**

1. We reject the null hypothesis when the p-value is smaller than the defined alpha p值小于设定的alpha值的时候拒绝原假设
2. ~~Hypothesis testing can only be used for large sample sizes~~
3. Hypothesis testing involves making an initial assumption, collecting data, and then testing the assumption statistically 假设检验包括设定一个初始的假设、收集数据、统计验证假设是否成立
4. ~~Hypothesis testing is <mark style="color:red;">not</mark> related to inferential statistics~~

### Choose the correct statements about descriptive statistics

**以下关于描述性统计正确的是**

1. Descriptive statistics provide simple summaries about the sample and the measures 描述性统计提供了对样本和评价标准的简要的总结
2. ~~Descriptive statistics are used to test hypotheses and make estimations~~
3. Descriptive statistics are used to describe the basic features of the data in a study 描述性统计是用来形容一个研究中数据的基本特征的
4. ~~Descriptive statistics <mark style="color:red;">cannot</mark> provide information about the mean, median, and mode.~~&#x20;

## Quiz 2

### Which of the following functions is used to introduce non-linearity in Deep learning models?

**以下哪个是深度学习模型的非线性函数**

1. ReLU
2. ~~Softmax~~
3. ~~Linear~~

### Assume your ML model predicts cats and not cat, which of the following arguments are correct?

**对正样本是猫的二分类模型，以下哪个说法是正确的**

1. If the model predicts not cat while the ground truth is not cat, we call that True Negative. 如果模型预测不是猫，并且也确实不是猫，那么是真负。True Negative
2. ~~If the model predicts not cat while the ground truth is cat, we call that <mark style="color:red;">False Positive</mark>~~ (False Negative)
3. ~~If the model predicts cat while the ground truth is not cat, we call that <mark style="color:red;">True Positive</mark>~~ (False Positive)
4. ~~If the model predicts cat while the ground truth is cat, we call that <mark style="color:red;">False Negative</mark>~~ (True Positive)

### Choose hyperparameters from the following answers?

**以下关于超参数说法正确的是**

1. Epochs
2. ~~Optimizer~~
3. Learning rate
4. Batches

### Choose the correct statements about Stochastic Gradient Descent?

**以下关于随机梯度下降说法正确的是**

1. Stochastic Gradient Descent (SGD) is an implementation of Gradient Descent that uses batches on each pass. SGD是GD的batch实现版本
2. ~~SGD uses <mark style="color:red;">the entire dataset</mark> to calculate the gradient of the cost function for each iteration of the training algorithm.~~
3. SGD is computationally faster and can also be used to escape local optima during training. SGD计算速度更快，并且能跳出局部最优解
4. ~~SGD can only be used for linear regression problems~~

### Choose the correct statements about Adam optimizer?

**以下关于Adam优化器的说法正确的是**

1. Adam is an optimization algorithm that can be used instead of the classical stochastic gradient descent procedure to update network weights iterative based on training data. Adam 是一种优化算法，可以代替经典的随机梯度下降过程，根据训练数据迭代更新网络权重。
2. Adam tends to focus on faster computation time, whereas other algorithms focus on data points. Adam更关注高效计算，但是其他算法关注的是对数据的刻画
3. ~~Adam is not suitable for problems that are large in terms of data/parameters.~~&#x20;
4. Adam combines the advantages of two other extensions of stochastic gradient descent: AdaGrad and RMSProp. Adam结合了AdaGrad和RMSProp优化器的优点

## Quiz 3

### What are the drawbacks of the random-walk and the node2vec algorithms

**随机游走和node2vec的缺点是什么**

1. Only uses structure features 只应用了结构化特征
2. ~~They do not support multi-label classification~~
3. ~~They are computationally efficient~~
4. Complicated to calculate all the embeddings 获得embedding很复杂

### Which of the following arguments are correct?

**以下说法正确的是**

1. The node degree feature is both an importance-based feature and a structure-based feature 节点度既是重要的特征，也是结构化特征
2. Katz index can calculate the relationships between two nodes even if those two nodes do not share any direct neighbors. Katz index可以计算任意两个节点的特征，即使这两个节点没有直接的共享的邻居节点
3. ~~The node degree feature is only a structure-based feature.~~&#x20;
4. ~~Katz index can only calculate the relationships between two nodes if they share direct neighbors.~~&#x20;

### Which of the following descriptions are correct for NMT?

**以下关于基于神经网络的机器翻译的说法正确的是？**

1. NMT performs better translation than SMT NMT的翻译效果比SMT好
2. ~~NMT stands for Non-Machine Translation~~
3. ~~NMT can only translate between two languages at a time.~~
4. It is difficult to understand and debug NMT-based systems NMT的可解释性不好

### Which of the following descriptions are correct for SMT?

**以下关于传统机器翻译的说法正确的是？**

1. ~~Statistical machine translation does <mark style="color:red;">not require</mark> a large amount of bilingual text~~
2. ~~Statistical machine translation is based on the rules of <mark style="color:red;">grammar and syntax</mark>~~&#x20;
3. Statistical machine translation is a machine translation paradigm where translations are generated based on statistical models whose parameters are derived from the analysis of bilingual text corpora. 统计翻译模型是基于统计模型生成翻译，参数是基于双向文本语料的
4. Statistical machine translation is a type of machine learning SMT是一种机器翻译

### Which of the following descriptions are correct for Beam Search Decoding?

**以下关于Beam Search说法正确的是**

1. Beam Search is a heuristic search algorithm that explores a graph by expanding the most promising node in a limited set. Beam Search 是启发性的搜索算法，是在有限的方向上探索最有可能的结果
2. ~~Beam Search is a greedy algorithm that selects the best option at each step as it attempts to find the <mark style="color:red;">overall</mark> best solution.~~&#x20;
3. Beam Search is used in many natural language processing applications, particularly for tasks that generate sequences. Beam Search被广泛应用在自然语言处理的应用中，特别是生成句子的任务
4. ~~Beam Search always <mark style="color:red;">guarantees</mark> to find the optimal solution.~~&#x20;
