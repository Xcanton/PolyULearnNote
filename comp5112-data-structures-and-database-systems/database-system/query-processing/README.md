# Query Processing

## 空间复杂度

<figure><img src="../../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

## [#li-ti](how-to-process-join-operation.md#li-ti "mention")-计算Nested-Loop的开销

<figure><img src="../../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

## [#li-ti-1](how-to-process-join-operation.md#li-ti-1 "mention")-计算Hash Join的开销

<figure><img src="../../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

* <mark style="color:red;">必须满足one pass，不然不可用Hash Join</mark>

## 例题-比较Block-Nested Loop和Hash Join并选择合适算法

<figure><img src="../../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (127).png" alt=""><figcaption><p>Solution</p></figcaption></figure>
