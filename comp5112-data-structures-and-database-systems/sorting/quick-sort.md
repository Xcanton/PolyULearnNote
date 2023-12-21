# Quick Sort

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption><p>pseudocode for Quick Sort</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption><p>pseudocode for Partition in Quick Sort</p></figcaption></figure>

* 将未排序数组的最后一个作为分隔判断标准，对前面数组是否大于pivot进行划分
* 将privot交换至合适位置
* 对大于pivot和小于pivot的未排序数组重复相同的动作
* 在逆序时，算法会退化成O（n^2）
