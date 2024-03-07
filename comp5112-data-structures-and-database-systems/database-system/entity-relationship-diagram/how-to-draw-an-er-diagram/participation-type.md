# Participation Type

在确定实体关系类型后，还需要考虑在关系到实体的过程中，能否为0，即能否部分实体不参与这个关系。

<figure><img src="../../../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption><p>Examples of different Participation Type</p></figcaption></figure>

## Total Participation（双线）

* 这部分表示，所有的实体参与到至少一个关系中。
* 是否上限是一，与是否是箭头有关，即关系类型。
* every entity in the entity set participates in at least one relationship in the relationship set

## Partial Participation（单线）

* 改部分表示，不一定所有实体都参与到关系中，即可以为0
* 是否能大于1，与是否是箭头有关，即关系类型
* some entities may not participate in any relationship in the relationship set
