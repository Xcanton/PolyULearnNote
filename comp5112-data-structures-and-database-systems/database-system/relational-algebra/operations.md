# Operations

## Basic Operations

<figure><img src="../../../.gitbook/assets/image (195).png" alt=""><figcaption><p>Basic Operations in Relational Algebra</p></figcaption></figure>

### Select

$$
\sigma：\sigma_{price > 0.8}(Product)
$$

* 从表中选择出复合条件的数据，可以搭配逻辑或和逻辑与使用
* 逻辑或可能导致空值

$$
\sigma_{price>8.5 \land brand="co"}(Product) \\ \sigma_{price>8.5 \lor brand="co"}(Product)
$$

### Project

$$
\Pi:\Pi_{name}(Product)
$$

* 从表中选择对应列（column）

### Cartesian Product（叉乘，笛卡尔积）

$$
\times:Customer \times Invoice
$$

* 笛卡尔积会保留两边相同的列名，并带上前缀，后续判断和选择的时候需要带上前缀。

<figure><img src="../../../.gitbook/assets/image (196).png" alt=""><figcaption><p>Result of Customer and Invoice's Cartesian Product</p></figcaption></figure>

* 笛卡尔积通常与Select和Project组合使用。

$$
\Pi_{prod\_id}(\sigma_{Customer.cust\_id=Invoice.cust\_id}(Customer \times Invoice))
$$

### Union

$$
\Pi_{{prod\_id}}(\sigma_{prod\_id\leq2}(Product))\cup\Pi_{prod\_id}(\sigma_{prod\_id=4}(Product))
$$

<figure><img src="../../../.gitbook/assets/image (188).png" alt=""><figcaption><p>Results of Union</p></figcaption></figure>

### Set Difference

$$
\Pi_{prod\_id}(Product)-\Pi_{prod\_id}(\sigma_{prod\_id=4}(Product))
$$

### Rename

$$
\rho_{Temp}(\Pi_{name}(\sigma_{price>8.0}(Product)))
$$

<figure><img src="../../../.gitbook/assets/image (217).png" alt=""><figcaption><p>Results of Rename</p></figcaption></figure>



## Other Operations

### Natural Join

$$
R\bowtie S: \\ \Pi_A(\sigma _{R.a1=S.a1, R.a2=S.a2,...R.ak=S.ak}(R \times S))
$$

### Set Intersection

<figure><img src="../../../.gitbook/assets/image (218).png" alt=""><figcaption></figcaption></figure>

### Assignment

<figure><img src="../../../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>

#### Insertion in Assignment

$$
Product \leftarrow Product \cup \{(5,"Soda","AB",7.5)\}
$$

#### Deletion in Assignment

$$
Product \leftarrow Product - \sigma_{price<7.0}(Product)
$$

### Generalized Project

$$
\Pi_{prod\_id, price*80\%\ as\ special\_price}(Product)
$$

### Aggregate Function

$$
\mathcal{G}:\\\mathcal{G}_{sum(amount)}(Invoice)\\\mathcal{G}_{max(price)}(Product)
$$

#### Aggregate function & Grouping

$$
_{cust\_id}\mathcal{G}_{sum(amount)}(Invoice)
$$
