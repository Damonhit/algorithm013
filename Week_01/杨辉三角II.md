# 杨辉三角 II

<https://leetcode-cn.com/problems/pascals-triangle-ii/>

## 代码

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>();
        res.add(1);
        for (int i = 0;i < rowIndex ; i++) {
            for (int j = i; j > 0; j--) {
                res.set(j, res.get(j) + res.get(j-1));
            }
            res.add(1);
        }

        return res;
    }
}
```
