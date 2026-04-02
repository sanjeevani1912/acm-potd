# POTD Day 12 : Remove Duplicates from Sorted List

### Description
Given the `head` of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

### Approach
I used a **Single Pass Iteration** to remove duplicates in linear time.
- Since the list is already sorted, all duplicate elements are guaranteed to be adjacent.
- I traversed the list starting from the `head`.
- For each node, I compared its value with the value of the next node.
- If they were the same, I skipped the next node by pointing the current node's `next` to the node after the next one.
- If they were different, I simply moved the current pointer forward.
- This effectively keeps only the first occurrence of every distinct value while maintaining the sorted order.

### Complexity
**Time: $O(n)$** — We traverse each node of the linked list exactly once.  
**Space: $O(1)$** — We perform the deletion in-place without using any extra data structures or memory.

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
    ListNode* deleteDuplicates(ListNode* head) {
        if (head == nullptr) return nullptr;
        
        ListNode* curr = head;
        while (curr != nullptr && curr->next != nullptr) {
            if (curr->val == curr->next->val) {
                // Skip the duplicate node
                curr->next = curr->next->next;
            } else {
                // Move to the next distinct element
                curr = curr->next;
            }
        }
        
        return head;
    }
};
```
### Screenshot
<img width="1045" height="547" alt="image" src="https://github.com/user-attachments/assets/f4c851d7-6117-4d8d-8e8c-7eced97bfc7e" />
