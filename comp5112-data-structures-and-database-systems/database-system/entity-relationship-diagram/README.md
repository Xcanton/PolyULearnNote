# Entity-Relationship Diagram

## 例题-小组作业管理系统

<figure><img src="../../../.gitbook/assets/image (210).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Solution</p></figcaption></figure>

* 每个学生必须参加一个组，每个组必须有2-4个学生，一对多，两边全参与
* 每个组提交的东西，包含在组内，不同的timestamp需要单独存储
* 每个组必须评分其他两个组，意味着每个组评价两个，被评价两个，属于多对多的全参与，不能为0，直接连个双实线
* 评分由于是同一个小组行为，所以用role表示

## 小测

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Solution</p></figcaption></figure>

* 一个导师可以在多个组，每个组必须有刚好一个老师，所以是老师1，教学组多，而且教学组不能为0
*
