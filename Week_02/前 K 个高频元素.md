# 前 K 个高频元素

## 思路

map维护元素个数

map放入最小栈，最小栈维护前k个高频元素

## 代码

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        PriorityQueue<Integer> queue = new PriorityQueue<>((o1, o2) -> map.get(o1) - map.get(o2));
        for (Integer num : map.keySet()) {
            if (queue.size() < k) {
                queue.offer(num);
            } else {
                if (map.get(num) > map.get(queue.peek())) {
                    queue.poll();
                    queue.offer(num);
                }
            }
        }
        int[] res = new int[k];
        for (int i = 0; i < k; i++) {
            res[i] = queue.poll();
        }
        return res;
    }
}
```
