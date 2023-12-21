# Stack（堆栈）

The Last-in First-out (LIFO) property，通常通过数组实现。

## Instance Variables

* S：用来实现堆栈的数组（an array of items）
* length：数组最大长度（the length of the array S）
* t：栈顶元素的位置，即堆栈内元素数量（the position of the top item）

## Operations

### push(e)

<figure><img src="../../../.gitbook/assets/image (138).png" alt=""><figcaption><p>pseudocode for Stack.push(e)</p></figcaption></figure>

* insert e to the top of the stack

### pop()

<figure><img src="../../../.gitbook/assets/image (139).png" alt=""><figcaption><p>pseudocode for Stack.pop()</p></figcaption></figure>

* extract the top item
* 可以不将弹出对应位置的元素置空

### size()

<figure><img src="../../../.gitbook/assets/image (198).png" alt=""><figcaption><p>pseudocode for Stack.size()</p></figcaption></figure>

* return the number of items stored

### isEmpty()

<figure><img src="../../../.gitbook/assets/image (136).png" alt=""><figcaption><p>pseudocode for Stack.isEmpty()</p></figcaption></figure>

* check wether the stack is empty

### top()

<figure><img src="../../../.gitbook/assets/image (137).png" alt=""><figcaption><p>pseudocode for Stack.top()</p></figcaption></figure>

* return the top item without removing it



