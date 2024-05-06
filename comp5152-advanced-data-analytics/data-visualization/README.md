# Data Visualization



* 标准的可视化方法（Standard Visualization Methods）
  * Plots
  * Scatter plots
* 高维数据可视化（High dimensional data）
  * Projection methods
* Data distributions
  * Histogram（直方图）
* 周期性数据Periodic data&#x20;
  * Spectral analysis

## 平行坐标图Parallel Coordinates

<figure><img src="../../.gitbook/assets/image (235).png" alt=""><figcaption></figcaption></figure>

将数据映射到线和纵轴上，每个特征是特征轴上的一个点。

好处：可以同时比较多个特征和变量，并展现其中的关系。（Parallel Coordinates Plots are ideal for comparing many variables together and seeing the relationships between them）

缺点：数据多的时候难以辨认（illegible when data are very dense）

## 箱线图Boxplot

箱线图是一种规范地展现数据分布的方式（A boxplot is a standardized way of displaying the dataset），组成箱线图有五个重要的要素：

*   Minimum（0th percentile Or Q0）

    the lowest data point in the data set excluding any outliers
*   Maximum（100th percentile or Q4）

    the highest data point in the data set excluding any outliers
*   Median（50th percentile or Q2）中位数

    the middle value in the data set
*   First quartile（25th percentile or Q1）

    also known as the lower quartile

    it is the median of the lower half of the dataset
*   Third quartile（75th percentile or Q3）

    also known as the upper quartile&#x20;

    it is the median of the upper half of the dataset

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

箱线图定义了一个四分位距离<mark style="color:red;">Interquartile range (IQR)</mark>，这个距离是<mark style="color:green;">从Q1到Q3两个点对应值的差</mark>。根据定义，可以算出允许离群点的最大值和最小值的数值：

$$
Maximum =Q_3+1.5 \times IQR\\
Minimum =Q_1-1.5 \times IQR
$$

对应地，将上四分位数和下四分位数组成的蓝色线段称为<mark style="color:red;">Whiskers</mark>。

箱线图的优点：

* 识别异常值
*   判断数据是否对称

    Identify if data is symmetrical
* 确定数据分布的紧密程度
* 查看数据是否有偏移（skewed）

## 直方图histogram

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

通过矩形反映数据的频率分布（frequency distribution）的图，其中矩形的宽度代表类间隔（class intervals），矩形的面积与该组频率呈正比。

Representation of a frequency distribution by means of rectangles whose width represent class intervals and whose areas are proportional to the corresponding frequencies.&#x20;

## 【<mark style="color:red;">VS</mark>】 Histogram vs. Boxplot

*   都是表示数据<mark style="color:red;">频率</mark>的图像

    Both are graphical representations for the <mark style="color:red;">frequency</mark> of data values
*   都能在描述数据的时候探索数据集中的趋势

    Describe the data and explore the central tendency
*   都适合表示中到大型的数据集

    Ideal to represent moderate to large amount of data
*   <mark style="color:green;">直方图</mark>更能够描述数据分布中<mark style="color:red;">潜在的概率分布</mark>规律

    Histograms prefer to determine the underlying probability distribution of a data
*   <mark style="color:green;">箱线图</mark>在<mark style="color:red;">比较多个数据集</mark>中更具有优势

    Boxplot are more useful when comparing between several data sets

## 热力图Heatmap

热力图是一种数据可视化的手段，可以以颜色量纲的形式展现数据大小。将数值转换成了颜色的表征

A heatmap is a data visualization technique that shows magnitude of a phenomenon as color in two dimensions. Replace numbers with colors

## 可视化中的维度爆炸问题 Curse of Dimensionality&#x20;

### 1.（Time）Complexity复杂度

主要关注时间复杂度。如果一个可视化需要关注的维度是\$$d\$$，那么多数方法需要的时间复杂度是\$$O(nd^2)\$$。其中n是样本的数量。

### 2. Number of Samples

假设一个维度需要9个样本刻画，那么维度的增加，会导致需要的样本数量是9的指数速度增长。

#### Common pitfall 认知陷阱

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

在数据可视化中，不一定增加维度会带来正向收益。

如果表征不足的话，常用的方式是增加特征。然而增加特征并不一定增加样本数量。这样会导致需要的样本数量与实际训练样本数量的偏差。导致潜在性能下降的可能性。

