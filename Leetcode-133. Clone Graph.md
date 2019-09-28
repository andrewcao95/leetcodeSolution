## Solution 1 DFS
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;

    public Node() {}

    public Node(int _val,List<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/
class Solution {
    public Node cloneGraph(Node node) {
        return helper(node, new HashMap<>());
    }
    
    public Node helper(Node node, HashMap<Node, Node> map) {
        List<Node> neighbors = new ArrayList<>();
        Node copy = new Node(node.val, neighbors);
        for (Node neighbor : node.neighbors) {
            if (!map.containsKey(neighbor)) {
                neighbors.add(helper(neighbor, map));
            } else {
                neighbors.add(map.get(neighbor));
            }
        }
        return map.get(node);
    }
}
```

## Solution 2 BFS

```java
class Solution {
    public Node cloneGraph(Node node) {
        HashMap<Node, Node> map = new HashMap<>();
        Queue<Node> queue = new LinkedList<>();
        queue.offer(node);
        map.put(node, new Node(node.val));
        while (!queue.isEmpty()) {
            Node cur = queue.poll();
            map.get(cur).neighbors = new ArrayList<>();
            for (Node neighbor : cur.neighbors) {
                if (!map.containsKey(neighbor)) {
                    map.put(neighbor, new Node(neighbor.val));
                    queue.offer(neighbor);
                }
                map.get(cur).neighbors.add(map.get(neighbor));
            }
        }
        return map.get(node);        
    }
}
```