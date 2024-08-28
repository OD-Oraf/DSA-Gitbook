# LRU Cache

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-06-29 at 7.41.06 PM.png" alt=""><figcaption></figcaption></figure>

```java
class LRUCache {

    private Map<Integer, Node> map;
    private int capacity;

    private Node left;
    private Node right;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        map = new HashMap<>();

        //left = LRU , right = most recent
        this.left = new Node(0, 0); // Dummy Head
        this.right = new Node(0, 0); // Dummy Tail
        this.left.next = this.right; // Set up doubly linked list
        this.right.prev = this.left;
    }

    public int get(int key) {
        if (map.containsKey(key)) {// key exisits , move to most recently used
            remove(map.get(key));
            insert(map.get(key));
            return map.get(key).val;
        } else {
            return -1;
        }
    }

    public void put(int key, int value) {
        if (map.containsKey(key)) {
            remove(map.get(key));// remove key to overwrite
        }
        map.put(key, new Node(key, value));
        insert(map.get(key));

        if (map.size() > capacity) {
            // remove from the list and delte the LRU from the hashmap
            Node lru = this.left.next;
            remove(lru);
            map.remove(lru.key);
        }
    }

    // remove node from list
    public void remove(Node node) {
        Node prev = node.prev;
        Node next = node.next;

        prev.next = next;
        next.prev = prev;
    }

    // insert node at right
    public void insert(Node node) {
        Node prev = this.right.prev;
        Node next = this.right;

        prev.next = node;
        next.prev = node;

        node.next = next;
        node.prev = prev;
    }

    private class Node {

        private int key;
        private int val;

        Node next;
        Node prev;

        public Node(int key, int val) {
            this.key = key;
            this.val = val;
        }
    }
}

```
