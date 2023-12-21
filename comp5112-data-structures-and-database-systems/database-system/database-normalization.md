# Database Normalization

## 小测-针对关系计算候选键和是否有多余元素

<figure><img src="../../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>

### 计算候选键

<figure><img src="../../.gitbook/assets/image (205).png" alt=""><figcaption></figcaption></figure>

* 找到一个SuperKey，满足它的外推集合是整个关系R
* 考虑这个SuperKey的子集，是否满足超键的定义
* 如果没有，那么这个键就是一个Candidate Key

### 寻找多余元素

<figure><img src="../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

* 对关系中的每一个关系
  *   计算其左边所有元素，是否是多余

      通过计算：左边除去这个元素 的超集是否包含右边所有元素。如果有那就是多余的元素。
  *   计算其右边元素是否是多余

      计算左边元素的超集（不包含该条关系），看是否能推导出右边的元素，如果能，那么该元素是多余元素。



## 例题-找到所有Candidate Key

<figure><img src="../../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (191).png" alt=""><figcaption><p>Solution</p></figcaption></figure>

* 从少到多寻找能够包括所有R中关系的集合，如果被包含，那么它的超集不用计算。
* 如果有一个关系，只在推到关系的左边，不在右边，那么Candidate Key必须包含它

## 例题-根据关系给出实例

<figure><img src="../../.gitbook/assets/image (203).png" alt=""><figcaption></figcaption></figure>

* 记得证明为什么满足
