# POTD Day 25 : Maximum Depth of Binary Tree

### Description
Given the `root` of a binary tree, return its maximum depth. A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

### Approach
I used a **Recursive Depth-First Search (DFS)** approach to solve this problem.
- The depth of a tree can be defined recursively:
  1. If the current node is `NULL`, the depth is 0 (Base Case).
  2. Otherwise, the depth is $1 + \max(\text{depth of left subtree}, \text{depth of right subtree})$.
- This "Bottom-Up" recursion calculates the height of each subtree and passes it back up to the root.



### Complexity
**Time: $O(n)$** — We visit each node in the binary tree exactly once.  
**Space: $O(h)$** — Where $h$ is the height of the tree. This space is used by the recursion stack. In the worst case (a skewed tree), $O(h) = O(n)$.

### Code
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 * int val;
 * TreeNode *left;
 * TreeNode *right;
 * TreeNode() : val(0), left(nullptr), right(nullptr) {}
 * TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 * TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        // Base case: If the node is null, depth is 0
        if (root == nullptr) {
            return 0;
        }
        
        // Recursive calls for left and right subtrees
        int leftHeight = maxDepth(root->left);
        int rightHeight = maxDepth(root->right);
        
        // The depth of the current node is 1 + the max of its subtrees
        return 1 + max(leftHeight, rightHeight);
    }
};
```

### Screenshot
<img width="1009" height="543" alt="image" src="https://github.com/user-attachments/assets/2f0e8747-6893-4f66-9962-5b491667fba9" />
