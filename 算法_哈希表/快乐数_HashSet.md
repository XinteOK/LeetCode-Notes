### LeetCode no.202
##### 两个要点：
- set判断是否得到循环
- 得到数的每一个*位数*

```java
class Solution {
	public boolean isHappy(int n) {
		HashSet<Integer> record = new HashSet<>();  
		//n=1和循环，满足一个就退出
		while(n != 1 && !record.contains(n)) {
			record.add(n);
			n = getNextNumber(n);
		}
	}
	private int getNextNumber(int n) {
		int res = 0;
		while(n > 0) {
			int temp = n % 10；
			res += temp * temp;
			n = n / 10; 
		}
		return res;
	}
}
```