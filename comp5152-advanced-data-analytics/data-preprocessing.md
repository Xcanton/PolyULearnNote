# Data Preprocessing

## 与处理中的常见问题

1. 空值或缺失值（Missing or incomplete data）
2. 错误的数值（Invalid data value）比如200岁的小学生
3. 名称标准化（Name and Address Standardization）
4. 非对称数据（Inconsistent data across enterprise systems）（male和man）
5. 异常值（Outliers）

## 数据预处理的步骤Major Tasks

### 数据清洗Data Cleaning

* 是对缺失值的填充、错误数据的修正和删除错误或无关的数据的过程。（The process of adding missing data and correcting, repairing, or removing incorrect or irrelevant data from a data set）
* 对不一致的数据进行修正（Correct all of the inconsistent data）
* 非常琐碎耗时，但是非常关键（Can be tedious, but still needed）

#### 缺失值填充

1.  均值填充（mean value）

    Normal distribution
2.  中位数填充（median value）

    Non-normal distribution
3.  众数填充（the most probable value）

    Regression或decision tree

#### 噪声数据（Noisy Data）

是非必要数据、不相关数据和特例数据的组合（unnecessary data points, irrelevant data, and data that’s more difficult to group together）

#### 分箱处理（对噪声进行平滑）

好处

1. 能够减少离散特征的数量（Binning method reduces the number of distinct values per attribute）
2. 能够提升算法的准确度（减少了噪声的干扰）（Improve accuracy for algorithms such as, decision tree inductions）

方法

* 邻居节点（Neighborhood，更多在图）
* 根据数值分布进行分桶（Sorted values are distributed into a number of “buckets”, bins）
* 移动平滑（Bin method perform local smoothing）通过均值、中位数、边界（数值用桶的上下界表示，选择距离近的上界或者下界）等条件进行限制（Smoothing by bin means/medians/boundaries）

#### 回归处理Regression method（处理噪声）

老师认为这里是处理噪声，但我觉得是构建新的特征，因为模型需要训练

* 线性回归或者多元线性回归的方式提取新的特征
* 通过高阶特征的方式提升准确度（Improve accuracy for the prediction）

#### 分类处理Clustering method（处理噪声）

好处是

* 异常值可以被检测（Outliers can be detected by clustering）
* 可以顺便移除无关数据（Remove the irrelevant data）

#### 数据差异Discrepancies

* 冗余的选项（Poorly designed data entry forms that have many optional fields）
* 人为错误（Human error in data entry）
*   人为故意错误（Deliberate errors）

    由于受访者不愿意透露某些信息（Respondents not wanting to divulge info about themselves）
*   数据衰减（Data decay）

    过时的居住地址等
* 格式不统一（Consistent use of codes）
* 内存溢出（Field overflow）

#### 检查metadata的好处

* 了解特征类型（What are the type and domain of each attribute）
* 知道特征的取值范围（Acceptable values for each attribute）
* 识别异常数据（Use descriptive statistics to identify data trends and identify anomalies）
* 可控的处理过程（Do all the values fall within the expected range）

### 数据整合Data Integration

需要整合多个数据源的数据（Require merge data from multiple data stores），好处是：

* 可以避免和减少冗余和数据不对齐（Careful integration can help reduce and avoid redundancies and inconsistencies in the resulting dataset）

#### 实体识别问题（Entity Identification Proble）

Schema和实体可能会导致冲突

#### 冗余和相关性数据（Redundancy and Correlation）

特征间可能存在相关性，如果完全相关可能会导致冗余特征。

需要对特征做出检验，以下是常见的检验方法：

* 假设检验（Hypothesis testing）
* Chi相关性检验（对类别特征）（Chi correlation test for nominal data）
* Correlation Coefficient for numeric data

### 数据降维Data Reduction

#### 为什么需要数据降维？

* 数据集庞大（Data set too huge）
* 详尽的数据分析和挖掘工作会占据大量的时间（Complex data analysis and mining on huge amount of data can take a long time）
* 全量数据的预处理是不适用或不灵活的（Impractical or infeasible）
* 下采样能够保证部分总体特征的获取（Impractical or infeasible）
  * 数量更少（Smaller in volume）
  * 与原数据分布和特征一致（Yet closely maintains the integrity of the original data）
  * 结果相近（More efficient yet produce the same (almost he same) analytical results）

#### PCA

### 数据转换Data Transformation

数据被转换或者合并成适合挖掘的格式（Data are transformed or consolidated into forms appropriate for mining）

* 指数变换
* 对数变换
* 幂变换
* 绝对值变换
*   Standardization

    适合高斯分布的特征

    能够统一量纲
*   Normalization

    分布相同，适合均匀分布的特征
