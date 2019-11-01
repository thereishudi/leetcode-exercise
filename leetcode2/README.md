## 解题思路
相当于合并两个链表值，用一个高位来存储进位，初始为零，终止条件为都扫描到空值和进位为零

## 代码实现
```java
public class problem2 {


    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode res = new ListNode(0);
        ListNode tem = res;
        int up = 0;
        while(!(l1 == null && l2 == null && up == 0)){
            int a = l1 == null?0: l1.val;
            int b = l2 == null?0:l2.val;
            tem.next = new ListNode((up+a+b)%10);
            up = (a+b+up)/10;
            tem = tem.next;
            l1 = l1 == null?l1:l1.next;
            l2 = l2 == null?l2:l2.next;
        }
        return res.next;
    }
}
```
