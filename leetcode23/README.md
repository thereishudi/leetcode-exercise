## 题目描述

合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

```
示例:

输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6
```



## 解题思路

由于之前已经做过将两个有序链表合并的提，用递归很好实现。

分治法：

1. 分解原问题为若干个子问题，这些子问题是原问题的规模较小的实例；
2. 递归求解这些子问题，如果规模足够小，则直接求解；
3. 合并这些子问题的解即可得到原问题的解。



## 实现代码

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists.length == 0){
            return null;
        }
        return mergeKLists(lists,0, lists.length-1);
    }

    private ListNode mergeKLists (ListNode[] lists, int left, int right) {
        if (left == right) {
            return lists[left];
        }
        int mid = (left + right) / 2;
        ListNode node1 = mergeKLists(lists, left, mid);
        ListNode node2 = mergeKLists(lists, mid+1, right);

        return mergeTwoList(node1, node2);
    }


    //采用递归的方式来合并两个有序链表
    //因为容易所以用递归
    private ListNode mergeTwoList(ListNode l1, ListNode l2) {
        if (l1 == null) {
            return l2;
        } else if (l2 == null) {
            return l1;
        } else if (l1.val >= l2.val) {
            l2.next = mergeTwoList(l1, l2.next);
            return l2;
        } else {
            l1.next = mergeTwoList(l1.next, l2);
            return l1;
        }
    }
}
```





