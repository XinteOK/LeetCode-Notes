### `HashSet` 简介

- `HashSet` ：纯粹的容器，只存值，无键 ，*自动去重*
```java
//常见API
//1.创建
HashSet<Integer> set = new HashSet<>();
//2.添加元素
set.add(5);
//3.判断元素是否存在
set.contains(5);
//4.删除元素
set.remove(5);
```

### 题解

- 去重，判断存在一般使用`HaspSet`
- 创建2个哈希表，一个存结果，一个存其中一组数据
- WARN:使用`HashSet`要*导包*
```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
    //防止传递空参数
        if(nums1 == null ||nums1.length == 0 ||nums2 ==null || nums2.length ==0)
            return new int[0];

        HashSet<Integer> result = new HashSet<>();
        HashSet<Integer> record = new HashSet<>();
        for(int i = 0;i < nums1.length;i++){
            record.add(nums1[i]);
        }
        for(int i = 0;i < nums2.length;i++){
            if(record.contains(nums2[i])){
                result.add(nums2[i]);
            }
        } 
    //结果要求是数组，创建一个新数组存结果
    int arr[] = new int[result.size()];
    int j = 0;
    for(int i : result){
        arr[j++] = i;
    }
    return arr;
    }
}
```