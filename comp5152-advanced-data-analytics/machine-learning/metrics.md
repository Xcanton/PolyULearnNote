# Metrics

## 混淆矩阵 Confusion Matrix

|     |    | 预测的                           |                               |
| --- | -- | ----------------------------- | ----------------------------- |
|     |    | 正类                            | 负类                            |
| 真实的 | 正类 | <p>True Positives<br>真正类</p>  | <p>False Negatives<br>假负类</p> |
|     | 负类 | <p>False Positives<br>假正类</p> | <p>True Negatives<br>真负类</p>  |

本质上混淆矩阵是分类模型预测结果的展示，可以通过混淆矩阵对分类模型的效果进行总结和归因，并且根据关注点不同衍生出不同的评价指标：

* Accuracy 准确率
  *   准确率是用来评估判断正确的正负样本同等重要的情况，它更关注是否判断准确，而对其中的类别没有特殊的关注。准确率适合用在样本均衡的数据上。

      Accuracy is used when the True Positives and True Negatives are more important. Accuracy is a better metric for Balanced Data
* Precision 精确率（不知道干嘛和准确率这么相近）
  *   精确率适合用于在假正样本更加重要的情况下，即对判断为正类事件判断错的代价很高的情况下。精确率更关注的是<mark style="color:green;">预测</mark>的正样本是否区分准确。

      Whenever False Positive is much more important use Precision
* Recall 召回率
  *   召回率适用于在假负样本更加重要的情况下，即对正样本误判代价很高的情况下。召回率更关注<mark style="color:green;">原本</mark>的正样本是否能被正确区分。

      Whenever False Negative is much more important use Recall
* F1-Score
  *   F1-score是衡量假负样本和假正样本同等重要的情况，并且该指标对样本不均衡的数据友好。

      F1-score is used when the False Negative and False Positives are important. Good for imbalanced data.

$$
Accuracy=\fr
$$
