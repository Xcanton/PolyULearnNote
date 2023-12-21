# How to Process a Query

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption><p>SQL Query Processing</p></figcaption></figure>

* sql语句先被解析成关系代数表达式
* 通过对数据的统计信息（多少数据，多少个block，数据类型是什么等）优化成预计损耗更小的作业图（Plan）
* 在执行引擎中，将作业图和实际数据计算得到结果
