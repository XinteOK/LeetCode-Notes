- 快慢指针的*相遇点* 到*环的起点* 的距离Z = *head*到*环的起点*的距离X,即X = Z.  
 1. 快指针和慢指针同时出发，快指针速度快，相遇时，使用一个index记录相遇点  ，一个回到头指针
 2. 然后二者同时出发，*再次相遇点* 就是*环的起点*
 ```java
 public class Solution {
	 public ListNode detectCycle(ListNode head){
		 ListNode = fast;
		 ListNode = slow;
		 while(fast != null && fast.next != null){
			 fast = fast.next.next;
			 slow = slow.next;
			 if(fast == slow){
				 ListNode index1 = fast;
				 ListNode index2 = head;
				 while(index1 != index2){
					 index1 = index1.next;
					 index2 = index2.next;
				 } 
				 return index1;
			 }
		 }
		 return null;
	 }
 }
 ```