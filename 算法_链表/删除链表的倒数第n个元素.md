- 快慢指针
- 快慢指针都得从`dummyhead`开始，否则删不了第1个元素
```java
//最先定义dummyhead
ListNode dummyhead = new ListNode();
dummyhead.next = head;
ListNode fast = dummyhead;
ListNode slow = dummmyhead;

//快指针先走n+1步
for(int i = 0;i <=n;i++){
	fast = fast,next;
}

while(fast != null){
	fast = fast.next;
	slow = slow.next;
}
slow.next = slow.next.next;
return dummyhead.next;
```