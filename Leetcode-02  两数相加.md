Leetcode-02  两数相加

给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807



==代码==

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        String str1="";
        String str2="";
        ListNode n1=l1;
        ListNode n2=l2;
        ListNode result=null;
        ListNode cur=null;
        boolean need=false;//是否需要进位
        while(n1!=null&&n2!=null){
            int newNum=(need)?n1.val+n2.val+1:n1.val+n2.val;
            if(newNum>9){
                need=true;
            }else{
                need=false;
            }
            if(result==null){
                result=new ListNode(newNum%10);
                cur=result;
            }else{
                cur.next=new ListNode(newNum%10);
                cur=cur.next;
            }
            n1=n1.next;
            n2=n2.next;
        }
        while(n1!=null){
            int newNum=(need)?n1.val+1:n1.val;
            need=(newNum>9)?true:false;
            cur.next=new ListNode(newNum%10);
            cur=cur.next;
            n1=n1.next;
        }
        while(n2!=null){
            int newNum=(need)?n2.val+1:n2.val;
            need=(newNum>9)?true:false;
            cur.next=new ListNode(newNum%10);
            cur=cur.next;
            n2=n2.next;
        }
        if(need)cur.next=new ListNode(1);
        return result;
    }
}
```

结果：

![1589641072571](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\1589641072571.png)