# Basic Concept

## Entity（实体）

* 与其他物体不同的，能够表征某类人、事、物的单位
* an object that is distinguishable from other objects
* 可能有属性（attributes）

### Entity Set（实体集，也就是表）

* a set of entities of the same type

## Primary Key（主键）

* 在实体集中用来标记实体区别的键
* the designer selects one of the candidate key(s) to be the primary key

## Relationship（关系）

* 实体之间的联系（an association among entities）
* It may have attributes.

## Relationship Set（关系集）

* a collection of relationships

## Attributes（属性）

* 用来描述实体或者实体拥有的特性
* description/property of an entity

### Simple Attribute

### Composite Attribute

* It contains multiple simple attributes
* 地址可能由省会、城市、街道等多个属性集合

### Multi-valued Attributes

* 对同一个实体可能出现多个点值，在某些时候需要单独维护一张表

### Derived Attributes

* 可以通过其他属性计算得出的
* 比如，年龄可以通过生日和当前日期计算得出

