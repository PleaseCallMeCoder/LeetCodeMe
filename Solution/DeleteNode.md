# 问题描述

写一个方法删除单链表的一个(非尾节点)节点，只提供对要删除节点的访问。

比如链表为 1 -> 2 -> 3 -> 4 给定要删除的节点为第三个，值为 3 ，执行结果应该为 1 -> 2 -> 4

# 方案v1.0

通常删除单链表某个节点的操作为修改其前一个节点的指针指向其后的节点。但道题并没有给我们什么上下文信息，所以我们只能将其下一个节点的信息赋值给它了。

```
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```
