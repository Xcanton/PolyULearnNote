# Relationship Type

总的来说，关系到实体只有两种方式，由于关系的存在至少双方，所以衍生出三种（四个）不同的组合。

## 关系到实体的类型

## 最多一个（单线可以为零）

* 用实线单箭头表示![](<../../../../.gitbook/assets/image (167).png>)
* 是否为零取决于参与程度，如果是全参与即不能为零，反之则是，如果是正好等于一的，采用双实线的箭头

### 无限制（单线可以为0，也可以对应多个）

* 采用直线连接![](<../../../../.gitbook/assets/image (168).png>)
* 是否为0取决于参与程度，如果是全参与即不能为零，反之则是，如果必须有一个以上的，采用双实线

## Relationship Type

### One-to-one Relationship

<figure><img src="../../../../.gitbook/assets/image (166).png" alt=""><figcaption><p>One-to-one Relationship</p></figcaption></figure>

* 在关系的两边都是指向实体的实线箭头。

### One-to-Many Relationship

<figure><img src="../../../../.gitbook/assets/image (169).png" alt=""><figcaption><p>One-to-Many Relationship</p></figcaption></figure>

* 用实线箭头指向One，用实线不带箭头连接Many。
* a loan is associated with at most one customer
* a customer can have several loans

### Many-to-Many Relationship

<figure><img src="../../../../.gitbook/assets/image (140).png" alt=""><figcaption><p>Many-to-Many Relationship</p></figcaption></figure>

* 通过两个实线分别连接两段的实体。

### Roles

<figure><img src="../../../../.gitbook/assets/image (141).png" alt=""><figcaption><p>Different Roles in work_for Relationship</p></figcaption></figure>

* 有时候，同一个实体会有不同的状态，在ER图中起到不同的作用。这种状态用角色（Role）进行描述。

### Identifying Relationship(Weak Entity Sets)

#### Weak Entity Set

* 该实体依赖于其他实体，比如员工小孩表依赖于员工表，一旦员工离职，那么它的小孩也不复存在
* an entity set without a primary key

<figure><img src="../../../../.gitbook/assets/image (142).png" alt=""><figcaption><p>Example of Identifying Relationship and Weak Entities</p></figcaption></figure>

* 对参与了弱关系的时候，弱实体（Weak Entity）和对应的关系需要用双框框起来
* 对弱实体，还需要补充一个特征作为主键，但由于是人工补充的，所以不是下划线标记，而是虚线标记
