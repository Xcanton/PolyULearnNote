# Machine Learning

## The general framework of Machine Learning

<figure><img src="../../.gitbook/assets/image (319).png" alt=""><figcaption></figcaption></figure>

### 基本术语 Basic Terminologies

*   Datasets

    A collection of data inputs that contain informative values about the problem to be solved
*   Samples/Instances

    The data points
*   Features/Variables

    The informative values
*   Targets/Labels

    The ground truths defined by experts or observed in the pasts
*   Models

    A mathematical model built from the datasets by machine learning algorithms
*   Hyperparameters

    Preset values needed to configure an ML algorithm

### 训练和测试的基本流程 Basic Procedure of Training and Testing

更大的训练集上训练可能得到更好的模型

the larger we make our training set the better model we may be able to obtain

更大的测试集上测试能够得到更致信的结论

the larger we make our test set the more confidence we will have towards our model

<figure><img src="../../.gitbook/assets/image (320).png" alt=""><figcaption></figcaption></figure>

*   Train set

    The portion of data that you used to create the model

    * The 'lectures' you gave to the machines so that they can learn from them
*   Test set

    The portion of data that you used to evaluate the model

    * The 'exams' you gave to the machines so you can evaluate their learning result

#### Adding a validation set

更多时候，我们会从（训练）数据中保留出小部分样本作为验证集，这部分数据对模型的训练起到了正向的重要作用。课件中提到的假设是：在测试集上验证一个通过验证集的模型。

Use the validation set to evaluate results from the training set. Then, use the test set to double-check your evaluation after the model has "passed" the validation set.&#x20;

<figure><img src="../../.gitbook/assets/image (321).png" alt=""><figcaption></figcaption></figure>

In this improved workflow:&#x20;

1.  选择在验证集上表现最优的模型

    Pick the model that does best on the validation set
2.  在测试集上二次验证

    Double-check that model against the test set

这个流程的合理性在于：<mark style="color:red;">减少了测试集的曝光</mark>

This is a better workflow because it creates fewer exposures to the test set.&#x20;

## Learning Algorithms (Types)

[supervised-learning.md](supervised-learning.md "mention")

[unsupervised-learning.md](unsupervised-learning.md "mention")

## Evaluation Metrics

[metrics.md](metrics.md "mention")

## Classic Models

[decision-tree.md](decision-tree.md "mention")

[svm.md](svm.md "mention")
