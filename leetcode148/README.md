## leetcode 148



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
    public ListNode sortList(ListNode head) {
        if(head == null) {
            return head;
        }  
        if (head.next == null) {  //递归退出条件：即链表被划分后只剩一个结点 
            return head;  
        }
        ListNode fast = head, slow = head, pre = head; //这里使用快慢指针 进行链表划分
        while (fast != null && fast.next != null) {
            pre = slow;
            slow = slow.next;
            fast = fast.next.next;
        }
        pre.next = null;     //划分结果是，fast为原链表尾.next， slow为划分后链表右半部分表头,pre为左半部分表尾结点，所以pre.next要为null
        ListNode l = sortList(head); //左半部分递归划分 
        ListNode r = sortList(slow); //右半部分递归划分
        return merge(l,r);  //合并链表 
    }

    public ListNode merge (ListNode l1, ListNode l2) {
        ListNode tHead = new ListNode(0);
        ListNode ans = tHead;
        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                tHead.next = l1;
                l1 = l1.next;
                tHead = tHead.next;
            } else {
                tHead.next = l2;
                l2 = l2.next;
                tHead = tHead.next;
            } 
        }
        if (l1 == null) {
            tHead.next = l2;
        } 
        else {
            tHead.next = l1;
        }
        return ans.next;
    }
}
```

