# POTD Day 8 : Reverse Linked List

### Description
Given the `head` of a singly linked list, reverse the list and return the reversed list.

### Approach
I used the **Iterative Three-Pointer** technique to reverse the list in a single pass.
- I maintained three pointers: `prev` (initially `NULL`), `curr` (starting at `head`), and `next_node` (to temporarily store the next node).
- While traversing the list, I saved the `curr->next` in `next_node`.
- I then flipped the `curr->next` pointer to point backwards to `prev`.
- Finally, I moved the `prev` and `curr` pointers one step forward.
- Once the loop finished, `prev` became the new head of the reversed list.



### Complexity
**Time: $O(n)$** — We traverse the entire list of $n$ nodes exactly once.  
**Space: $O(1)$** — We only use three pointer variables, regardless of the list's length.

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
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        
        while (curr != nullptr) {
            ListNode* next_node = curr->next; // Store the next node
            curr->next = prev;               // Flip the current pointer
            prev = curr;                     // Move prev forward
            curr = next_node;                // Move curr forward
        }
        
        return prev; // prev is the new head
    }
};
```

### Screenshot
<img width="1017" height="543" alt="image" src="https://github.com/user-attachments/assets/8dbcaeb5-faa8-4767-a915-b0facaf9f6e3" />
