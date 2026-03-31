# POTD Day 10 : Middle of the Linked List

### Description
Given the `head` of a singly linked list, return the middle node of the linked list. If there are two middle nodes, return the second middle node.

### Approach
I used the **Tortoise and Hare (Slow and Fast Pointers)** algorithm to find the middle node in a single pass.
- I initialized two pointers, `slow` and `fast`, both starting at the `head`.
- I moved the `fast` pointer two steps at a time and the `slow` pointer one step at a time.
- By the time the `fast` pointer reached the end of the list, the `slow` pointer was positioned exactly at the middle.
- This is more efficient than a two-pass approach (counting length then iterating) because it only requires one traversal.



### Complexity
**Time: $O(n)$** — We traverse the list once.  
**Space: $O(1)$** — We only use two pointer variables.

### Code
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 * int val;
 * ListNode *next;
 * ListNode() : val(0), next(nullptr) {}
 * ListNode(int x) : val(x), next(nullptr) {}
 * ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }
        
        return slow;
    }
};
```

### Screenshot
<img width="923" height="548" alt="image" src="https://github.com/user-attachments/assets/2d77c447-8d71-470c-9ebb-c4508b275610" />

