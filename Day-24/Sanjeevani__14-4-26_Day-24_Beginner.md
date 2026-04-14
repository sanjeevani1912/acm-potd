# POTD Day 24 : Find Center of Star Graph

### Description
There is an undirected star graph consisting of $n$ nodes. A star graph is a graph where there is one center node and exactly $n - 1$ edges that connect the center node with every other node. Given the 2D integer array `edges`, find and return the center node.

### Approach
I used a **Constant Time Comparison** approach by exploiting the properties of a star graph.
- In a star graph, the center node is the only node that appears in every single edge.
- Since the problem guarantees a valid star graph, I only need to look at the first two edges.
- The center node must be the node that is common between `edges[0]` and `edges[1]`.
- I simply checked if the first node of the first edge matches either node of the second edge. If it does, that's the center; otherwise, the second node of the first edge must be the center.

### Complexity
**Time: $O(1)$** — We only check the first two edges of the input, regardless of how many nodes or edges exist.  
**Space: $O(1)$** — No extra data structures are used.

### Code
```cpp
class Solution {
public:
    int findCenter(vector<vector<int>>& edges) {
        // The center node must appear in every edge.
        // Therefore, it must be common to the first two edges.
        int u1 = edges[0][0], v1 = edges[0][1];
        int u2 = edges[1][0], v2 = edges[1][1];
        
        if (u1 == u2 || u1 == v2) {
            return u1;
        }
        
        return v1;
    }
};
```

### ScreenShot
<img width="952" height="539" alt="image" src="https://github.com/user-attachments/assets/d72fe087-175b-48f3-8826-fb57c188d528" />
