# 杨辉三角

<https://leetcode-cn.com/problems/pascals-triangle/>

## 代码

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();
        if (numRows == 0) {
            return res;
        }
        res.add(new ArrayList<>());
        res.get(0).add(1);
        for (int i = 1; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();
            row.add(1);
            List<Integer> pre = res.get(i - 1);
            for (int j = 0; j < pre.size() - 1; j++) {
                row.add(pre.get(j) + pre.get(j + 1));
            }
            row.add(1);
            res.add(row);
        }
        return res;
    }
}
```
