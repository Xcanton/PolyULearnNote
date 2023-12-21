# Storage Hierarchy

## Storage Type

### Primary Storage

Faster but volatile(断电无法存储，需要维持工作状态)

E.g., CPU cache and main memory

Loses content when power is switched off

### Secondary Storage

non-volatile, slower higher capacity

E.g., flash memory, magnetic disks

Content persists even when power is switched off

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

## Data Access Time

$$
Access time = b* t_T + s*t_S
$$

* b: the number of disk block transfers
* s: the number of seeks
* tT: time to transfer one disk block
* tS: time to seek one disk block

如果是遍历链表的话，b为链表长度，s为1，因为只需要找到一次链表头，可以按照链表顺序遍历



