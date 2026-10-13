## KMP算法的作用
- 当出现字符串不匹配时，可以知道一部分之前已经匹配的文本内容，可以利用这些信息避免从头开始匹配。
- 也就是利用已经匹配的部分的相等的前后缀，已经匹配的部分的*最大相等的前后缀长度*是多少，就可以少匹配几个字符。
## next数组
-  用来辅助KMP算法 
- 可通过递推计算得出
- `next[j]` 表示：当模式串的第j个字符不匹配时，应该回退到的*下标位置*。本质上是，下标j之前的子串（`P[0..j-1]`）的*最长相等前后缀的长度*。
## 时间复杂度
- O(m+n)
## 例题：
- LeetCode28.找出字符串中第一个匹项想的下标
```JAVA
class Solution {
    public int strStr(String haystack, String needle) {
        //特殊情况:needle为空
        if(needle.length() == 0) return 0;
        
        int[] next = new int[needle.length()];
        getNext(next, needle);

        //KMP匹配过程
        int j = 0;
        for(int i = 0; i < haystack.length(); i++) {
            while(j > 0 && needle.charAt(j) != haystack.charAt(i)) {
                j = next[j - 1];
            }
            if(needle.charAt(j) == haystack.charAt(i)) {
                j++;
            }
            if(j == needle.length()) {
                return i - needle.length() + 1;
            }
        }
        return -1;	
    }

    //构造next数组，提到类里面，不能嵌套在strStr中
    private void getNext(int[] next, String s) {
        //1.初始化
        int j = 0; // j前缀末尾，i后缀末尾
        next[0] = j;
        
        // i从1开始！！，和前面的i不是一个含义
        for(int i = 1; i < s.length(); i++) {
            //字符不匹配时
            while(j > 0 && s.charAt(i) != s.charAt(j)) {
                j = next[j - 1];
            }
            //字符匹配时
            if(s.charAt(i) == s.charAt(j)) {
                j++;
            }
            next[i] = j;
        } 
    }
}

```