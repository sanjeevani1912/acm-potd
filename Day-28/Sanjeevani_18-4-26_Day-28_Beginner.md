# POTD Day 28 : Subtree of Another Tree

### Description
Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values as `subRoot`, and `false` otherwise.

### Approach
I used a **Double Recursive** approach to solve this problem.
- **Main Recursion:** I traversed the `root` tree. For every node I encountered, I treated it as a potential start of the subtree and called a helper function to check for equality.
- **Helper Function (isIdentical):** This function checks if two trees are exactly the same. 
  1. If both nodes are NULL, they are identical.
  2. If only one is NULL or the values differ, they are not identical.
  3. Otherwise, I recursively check if the left subtrees match and the right subtrees match.
- If the current node doesn't match `subRoot`, I recursively call the main function on the left and right children of `root`.



### Complexity
**Time: O(m * n)** — Where m is the number of nodes in `root` and n is the number of nodes in `subRoot`. In the worst case, we check the `isIdentical` condition for every node in the main tree.  
**Space: O(h)** — Where h is the height of the `root` tree. This is the space used by the recursion stack.

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
    bool isIdentical(TreeNode* s, TreeNode* t) {
        if (!s && !t) return true;
        if (!s || !t || s->val != t->val) return false;
        
        return isIdentical(s->left, t->left) && isIdentical(s->right, t->right);
    }

    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        if (!root) return false;
        
        // Check if trees are identical starting from current root
        if (isIdentical(root, subRoot)) return true;
        
        // Otherwise, look for the subRoot in left or right subtrees
        return isSubtree(root->left, subRoot) || isSubtree(root->right, subRoot);
    }
};
```

### Screenshot
<img width="1007" height="551" alt="image" src="https://github.com/user-attachments/assets/2123fa17-7a16-410b-b258-c57eaaab4b5f" />

