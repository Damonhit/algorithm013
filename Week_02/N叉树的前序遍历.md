# N叉树的前序遍历

## 代码

**递归：**

```java
class Solution {
    public List<Integer> preorder(Node root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) {
            return res;
        }
        return preOr(root, res);
    }

    private List<Integer> preOr(Node root, List<Integer> res) {
        if (root == null) {
            return res;
        }
        res.add(root.val);
        for (Node node : root.children) {
            preOr(node, res);
        }
        return res;
    }
}
```

**迭代：**

```java
class Solution {
    public List<Integer> preorder(Node root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) {
            return res;
        }
        Stack<Node> stack = new Stack<>();
        stack.push(root);
        while (!stack.isEmpty()) {
            Node node = stack.pop();
            res.add(node.val);
            Collections.reverse(node.children);
            for (Node child : node.children) {
                stack.push(child);
            }
        }
        return res;
    }
}
```
