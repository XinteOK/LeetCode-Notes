- 两个都是“模拟”题

- LeetCode344
- 双指针

```java
class Solution {
    public void reverseString(char[] s) {
        int l = 0; int r = s.length - 1;
        char temp;

        while(l < r) {
            temp = char[l];
            char[l] = char[r];
            char[r] = temp;
            l++;
            r--;
        }
    }
}
```

- LeetCode541
- 双指针

```java
class Solution {
    public String reverseStr(String s, int k) {
        char[] ch = s.toCharArray();
		//将字符串转换为字符数组
        for(int i = 0;i < ch.length;i+=2*k){
            int start = i;
            int end = Math.min(ch.length - 1,start + k - 1);//题目条件
            while(start < end){ 
                char temp = ch[start];
                ch[start] = ch[end];
                ch[end] = temp;
                
                start++;
                end--;
            }//反转逻辑
        }
        return new String(ch);
    }
}
```