## merge-two-sorted-lists



#### 题目描述

将两个升序链表合并为一个新的 **升序** 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。



#### 示例

**示例 1：**

```
输入：l1 = [1,2,4], l2 = [1,3,4]
输出：[1,1,2,3,4,4]
```

**示例 2：**

```
输入：l1 = [], l2 = []
输出：[]
```

**示例 3：**

```
输入：l1 = [], l2 = [0]
输出：[0]
```



#### 解决方案

```js
var mergeTwoLists = function(l1, l2) {
    let node = new ListNode(), p = node
	// 设置一个保护节点
    
    while (l1 !== null && l2 !== null) { // 这里只能是 &&, 如果是||的话, 当一方的val为空就无法继续
        if (l1.val < l2.val) {
            p.next = l1
            l1 = l1.next
        } else {
            p.next = l2
            l2 = l2.next
        }
        p = p.next
    }

    // 若一方为空, 跳出循环, 让 p.next 指向另外不为空的一方
    if (l1 === null) p.next = l2
    if (l2 === null) p.next = l1
    
    // p 指向 node, 操作p来改变node, 按照代码逻辑下来, p.next是最后一次放进node的节点, 那就应该返回node.next
    return node.next
};
```



#### 执行结果

![image-20211121023752190](image/image-20211121023752190.png)