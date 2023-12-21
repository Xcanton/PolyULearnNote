# Relational Algebra

## 例题-关系代数表达式有什么sql不能表达

<figure><img src="../../../.gitbook/assets/image (212).png" alt=""><figcaption></figcaption></figure>

* 关系代数表达式不允许重复数据
* 不能够创建和删除表
* 不能够指定数据类型
* 不能够对数据排序

## 例题-用关系代数表达式表达Query

<figure><img src="../../../.gitbook/assets/image (213).png" alt=""><figcaption></figcaption></figure>

$$
\Pi_{StationID}(Station) - \\ \Pi_{StationID}(\sigma_{Date(DateTime)='2023-11-07'}(Windspeed))
$$

$$
\Pi_{StationID}(\sigma_{Date(DateTime)='2023-11-07' }(Temperature))-\\ \Pi_{StationID}(\sigma_{Date(DateTime)='2023-11-07' \land Tvalue \leq 30}(Temperature))
$$
