## KMP算法的作用
- 当出现字符串不匹配时，可以知道一部分之前已经匹配的文本内容，可以利用这些信息避免从头开始匹配。
- 属于是一个优化算法
## next数组
- 利用**前缀表**来实现记录：当模式串与主串不匹配时，模式串要回退的位置
- 即用来记录：下标i（包括i）之前的的字符串中，有多大长度的相同前后缀
## 时间复杂度
- O(m+n)
## 例题：
- LeetCode28.找出字符串中第一个匹项想的下标
```JAVA
class Solution {
	public int strStr(String haystack, String needle) {
		//特殊情况:needle为空
		if(needle.length() == 0) return 0;
		
		//构造next数组主要三步
		//1.初始化
		//2.处理前后缀不相同的情况
		//3.处理前后缀相同的情况
		int next = new int[needle.length()];
		getNext(next,needle);
		private void getNext (int[] next, String s) {
			//1.初始化
			int j = 0;//定义两个指针j:指向前缀末尾 i:指向后缀末尾
			next[0] = j;//未开始计算，全为0
			
			for(int i = 0; i<s.length(); i++) {
				//2.前后缀不匹配while
				while(j>0 && s.charAt(i)!=s.charAt(j)) {
					j = next[j - 1];//j回退，遇见冲突找前一个
				}
				//3.匹配if
				if(s.charAt(i)==s.charAt(j)) {
					j++;
				}
				//存入next数组
				next[i] = j;
			} 
		}
		//strStr()
		int j = 0;
		for(int i = 0;i < haystack.length();i++) {
			while(j>0 && needle.charAt(j) != haystack.chaAt(i))
				j = next[j - 1];
			if(needle.charAt(j) == haystack.charAt(i))
				j++;
			if(j == needle.length())
				return i - needle.length() + 1;
		}
		return -1;	
	}
}
```