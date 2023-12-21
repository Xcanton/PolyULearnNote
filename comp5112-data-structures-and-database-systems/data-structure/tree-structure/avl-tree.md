# AVL Tree

由于二叉树可能由于深度不同导致时间复杂度退化，所以引入 height-balance进行优化，具体算法是：

$$
hb(x)=height(x.left) - height(x.right)
$$

$$
height(nullptr) = -1
$$

那么，AVL Tree的高也是固定的数值：

$$
h \leq \log_{\phi} {n},\ \phi=1.618
$$

所以，搜索、插入、删除的时间复杂度和树的高度都满足：

$$
O(\log{n})
$$

## AVL Tree旋转

### 左旋Left Rotation

<figure><img src="../../../.gitbook/assets/image (105).png" alt=""><figcaption><p>Example for Left Rotation</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (109).png" alt=""><figcaption><p>pseudocode for Left Rotation</p></figcaption></figure>

* 如果hb值为-2，意味着左侧树比右侧树矮，即右侧失衡，需要进行左旋
* 即将右子树旋转到root节点（逆时针旋转）

### 右旋Right Rotation

<figure><img src="../../../.gitbook/assets/image (107).png" alt=""><figcaption><p>Examples for Right Rotation</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (108).png" alt=""><figcaption><p>pseudocode for Right Rotation</p></figcaption></figure>

## Insertion

<figure><img src="../../../.gitbook/assets/image (110).png" alt=""><figcaption><p>Insertion Situations</p></figcaption></figure>

插入需要对插入位置分情况讨论，插入后需要做对应的旋转：

* Outside cases: do a single rotation
  * (i):  left rotation
  * (ii): right rotation
* Inside cases: do a double rotation
  * (iii): do a left rotation, then do a right rotation
  * (iv): do a right rotation, then do a left rotation
* 总之，内侧插入的情况就是，插入左侧右节点的就做左旋然后右旋，右侧左节点的就是右旋再左旋。

## Deletion

分情况判断：

* 如果没有子节点，那么直接删除不多逼逼
* 如果有一个子节点，那么将子节点顶到自身位置
* 如果有两个子节点，那么从右子树中抽取最小的节点，作为新的主节点

在进行完删除以后，将新的树重新排列height-balance value，并且根据AVL树规则进行左旋或右旋。
