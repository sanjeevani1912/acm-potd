# POTD Day 27 : Diameter of Binary Tree

### Description
Given the `root` of a binary tree, return the length of the diameter of the tree. The diameter is the length of the longest path between any two nodes in a tree, represented by the number of edges between them. This path may or may not pass through the root.

### Approach
I used a **Recursive DFS** approach to solve this problem efficiently. 
- While the goal is to find the diameter, the easiest way to do this is to calculate the **height** of each node's subtrees.
- For any given node, the longest path passing through it is the sum of the heights of its left and right subtrees.
- I maintained a global variable `diameter` to keep track of the maximum path found during the recursion.
- The recursive function returns the height of the current node (1 + max(leftHeight, rightHeight)) to its parent, while simultaneously updating the global diameter with the value (leftHeight + rightHeight).
### Complexity
**Time: $O(n)$** — We visit each node in the tree exactly once.  
**Space: $O(h)$** — Where $h$ is the height of the tree, used by the recursion stack. In a balanced tree, this is $O(\log n)$; in a skewed tree, it is $O(n)$.

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
    int diameter = 0;

    int calculateHeight(TreeNode* node) {
        if (node == nullptr) return 0;

        // Recursively find the height of left and right subtrees
        int leftHeight = calculateHeight(node->left);
        int rightHeight = calculateHeight(node->right);

        // Update the global diameter if the path through this node is longer
        diameter = max(diameter, leftHeight + rightHeight);

        // Return the height of this node to the parent call
        return 1 + max(leftHeight, rightHeight);
    }

    int diameterOfBinaryTree(TreeNode* root) {
        calculateHeight(root);
        return diameter;
    }
};
```

### Screenshot
<img width="976" height="548" alt="image" src="https://github.com/user-attachments/assets/e71d17c7-8d08-4b73-a2bb-3e31902fb960" />
