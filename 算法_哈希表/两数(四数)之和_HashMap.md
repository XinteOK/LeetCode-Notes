### `HashMap`简介
- 键值对容器
- `key`唯一，`value`可重复
```java
// 1. 创建
HashMap<Integer, Integer> map = new HashMap<>();

// 2. 存：key-value
map.put(1, 100);

// 3. 取：通过key拿value，无key返回null
map.get(1); 

// 4. 安全取值：无key返回默认值0
map.getOrDefault(1, 0);

// 5. 判断key是否存在
map.containsKey(1);
```

- **两数之和题解已发布**：[两数之和](https://leetcode.cn/problems/two-sum/solutions/3968640/meng-kai-shi-de-di-fang-javajie-fa-by-fl-amlv)
- **四数之和**：[四数之和](https://leetcode.cn/problems/4sum-ii/solutions/3970879/javajie-fa-shi-yong-hashmap-by-flamboyan-3l2f)