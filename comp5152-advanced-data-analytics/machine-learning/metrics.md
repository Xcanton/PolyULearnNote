# Metrics

## 混淆矩阵 Confusion Matrix

|     |    | 预测的                           |                               |
| --- | -- | ----------------------------- | ----------------------------- |
|     |    | 正类                            | 负类                            |
| 真实的 | 正类 | <p>True Positives<br>真正类</p>  | <p>False Negatives<br>假负类</p> |
|     | 负类 | <p>False Positives<br>假正类</p> | <p>True Negatives<br>真负类</p>  |

本质上混淆矩阵是分类模型预测结果的展示，可以通过混淆矩阵对分类模型的效果进行总结和归因，并且根据关注点不同衍生出不同的评价指标：

* <mark style="color:red;">Accuracy</mark> 准确率
  *   准确率是用来评估<mark style="color:red;">判断正确的正负样本同等重要</mark>的情况，它更关注是否判断准确，而对其中的类别没有特殊的关注。准确率适合用在样本均衡的数据上。

      Accuracy is used when the True Positives and True Negatives are more important. Accuracy is a better metric for Balanced Data
* <mark style="color:red;">Precision</mark> 精确率（不知道干嘛和准确率这么相近）
  *   精确率适合用于在<mark style="color:red;">假正样本</mark>更加重要的情况下，即对判断为正类事件判断错的代价很高的情况下。精确率更关注的是<mark style="color:green;">预测</mark>的正样本是否区分准确。

      Whenever False Positive is much more important use Precision
* <mark style="color:red;">Recall</mark> 召回率
  *   召回率适用于在<mark style="color:red;">假负样本</mark>更加重要的情况下，即对正样本误判代价很高的情况下。召回率更关注<mark style="color:green;">原本</mark>的正样本是否能被正确区分。

      Whenever False Negative is much more important use Recall
* <mark style="color:red;">F1-Score</mark>
  *   F1-score是衡量<mark style="color:red;">假负样本和假正样本同等重要</mark>的情况，并且该指标对样本不均衡的数据友好。

      F1-score is used when the False Negative and False Positives are important. Good for imbalanced data.

$$
Accuracy=\frac {TN + TP} {TN + FP + FN + TP}
$$

$$
Precision= \frac {TP} {TP+FP}
$$

$$
Recall= \frac {TP} {TP+FN}
$$

$$
F1\_Score= 2 * \frac {Recall * Precision} {Recall + Precision}
$$

## ROC Curve & AUC

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

ROC曲线的横坐标是假正率（False Positive Rate, FPR），纵坐标是真正率（True Positive Rate, TPR），是用来衡量分类模型在不同的阈值下的表现。

AUC的全称是`Area Under the Curve`，意思是ROC曲线下的面积，即是可以达到的模型能力。这个指标课件上说是用来衡量分类模型的性能的。

{% hint style="info" %}
AUC实际上的物理意义是：取一个正样本和一个负样本，都经过模型得出一个打分，正样本评分高于负样本评分的概率。
{% endhint %}

根据真实的物理意义，可以将样本的评分从小到大排序，从1开始的索引。如果有`M`个正样本、有`N`个负样本，那么AUC的计算就变成不在最小的M部分的频率。

$$
AUC = \frac {\sum^M_i {rank(positive_i)} -\frac {M(M+1)} 2} {M \times N}
$$

## 均方差和标准差 MSE & RMSE

MSE对大的预测误差给予了更高的惩罚力度

$$
MSE=\frac 1 N \sum^N_{i=1} (y_i-\hat{y_i})^2
$$

## 平均绝对误差 MAE

MAE认为所有误差同等重要

$$
MAE=\frac 1 N \sum^N_{i=1} |y_i-\hat{y_i}|
$$
