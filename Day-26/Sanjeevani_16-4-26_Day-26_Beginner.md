# POTD Day 26 : Invert Binary Tree

### Description
Given the `root` of a binary tree, invert the tree (create a mirror image) and return its root.

### Approach
I used a **Recursive Post-order Traversal** approach to solve this.
- The core logic is to swap the left and right children of every node in the tree.
- **Recursive Step:** 1. Base Case: If the current node is `NULL`, return `NULL`.
  2. Recursively call the function for the left child and the right child.
  3. Swap the left and right pointers of the current node.
- This ensures that we work from the leaves up to the root, effectively mirroring the entire structure.



### Complexity
**Time: $O(n)$** — We visit every node in the tree exactly once.  
**Space: $O(h)$** — Where $h$ is the height of the tree, representing the maximum depth of the recursion stack. In a balanced tree, this is $O(\log n)$; in a skewed tree, it is $O(n)$.

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
    TreeNode* invertTree(TreeNode* root) {
        // Base case: if the tree is empty
        if (root == nullptr) {
            return nullptr;
        }

        // Recursively invert the subtrees
        invertTree(root->left);
        invertTree(root->right);

        // Swap the left and right children
        TreeNode* temp = root->left;
        root->left = root->right;
        root->right = temp;

        return root;
    }
};
```

### Screenshot
<img width="831" height="552" alt="image" src="https://github.com/user-attachments/assets/642ee7b3-b5df-40ab-ab2d-c05471ee1b00" />

