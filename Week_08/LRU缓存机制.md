# LRU缓存机制

## 代码

```java
class LRUCache {

    Map<Integer,Node> cache;
    Node head, tail;
    int capacity;
    int size = 0;

    public LRUCache(int capacity) {
        cache = new HashMap<>();
        head = new Node();
        tail = new Node();
        head.next = tail;
        tail.pre = head;
        this.capacity = capacity;
    }
    
    public int get(int key) {
        Node node = cache.get(key);
        if (node == null) {
            return -1;
        }
        moveToHead(node);
        return node.value;
    }
    
    public void put(int key, int value) {
        Node node = cache.get(key);
        if (node == null) {
            if (size == capacity) {
                Node rm = removeTail();
                cache.remove(rm.key);
                size--;
            }
            Node newNode = new Node(key, value);
            addToHead(newNode);
            cache.put(key, newNode);
            size++;
        } else {
            node.value = value;
            moveToHead(node);
        }
    }

    public void moveToHead(Node node) {
        removeNode(node);
        addToHead(node);
    }

    public void removeNode(Node node) {
        node.pre.next = node.next;
        node.next.pre = node.pre;
    }

    public void addToHead(Node node) {
        node.next = head.next;
        node.pre = head;
        head.next.pre = node;
        head.next = node;
    }

    public Node removeTail() {
        Node rm = tail.pre;
        removeNode(rm);
        return rm;
    }

    class Node {
        int key, value;
        Node pre, next;
        Node() {}
        Node(int k, int v) {
            this.key = k;
            this.value = v;
        }
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```