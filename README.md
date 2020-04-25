# Palindrome Linked List
## https://leetcode.com/problems/palindrome-linked-list



# Implementation :
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
    public boolean isPalindrome(ListNode head) {
        if(head == null || head.next == null)
            return true;
        
        ListNode p1 = clone(head);
        ListNode p2 = reverse(head);
        while(p1 != null) {
            if(p1.val != p2.val)
                return false;
            p1 = p1.next;
            p2 = p2.next;
        }
        return true;
    }
    
    private ListNode clone(ListNode head) {
        ListNode cloneHead = null;
        ListNode prev = null;
        ListNode current = head;
        while(current != null) {
            ListNode listnode = new ListNode(current.val);
            if(cloneHead == null) {
                cloneHead = listnode;
            }
            if(prev != null) {
                prev.next = listnode;
            }
            prev = listnode;
            current = current.next;
        }
        return cloneHead;
    }
    
    private ListNode reverse(ListNode head) {
        ListNode current = head;
        ListNode prev = null;
        while(current != null) {
            ListNode tmp = current.next;
            current.next = prev;
            prev = current;
            current = tmp;
        }
        return prev;
    }
}
```
