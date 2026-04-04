# POTD Day 14 : Palindrome Linked List

### Description
Given the `head` of a singly linked list, return `true` if it is a palindrome or `false` otherwise.

### Approach
I used the **Middle-Reverse-Compare** strategy to solve this in $O(n)$ time and $O(1)$ space.
- I found the middle of the linked list using the **Slow and Fast pointer** (Tortoise and Hare) technique.
- I reversed the second half of the linked list starting from the middle node.
- I then compared the first half of the list with the reversed second half node-by-node.
- If all values matched, the list is a palindrome.
- This approach is optimal as it avoids using extra space (like an array or stack) to store node values.



### Complexity
**Time: $O(n)$** — We traverse the list to find the middle, reverse the second half, and compare the two halves. Each step is linear.  
**Space: $O(1)$** — The reversal is done in-place, and we only use a few pointer variables.

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
    bool isPalindrome(ListNode* head) {
        if (!head || !head->next) return true;
        
        // 1. Find the middle
        ListNode *slow = head, *fast = head;
        while (fast->next && fast->next->next) {
            slow = slow->next;
            fast = fast->next->next;
        }
        
        // 2. Reverse the second half
        slow->next = reverseList(slow->next);
        slow = slow->next;
        
        // 3. Compare the halves
        ListNode* dummy = head;
        while (slow) {
            if (dummy->val != slow->val) return false;
            dummy = dummy->next;
            slow = slow->next;
        }
        
        return true;
    }
    
private:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while (curr) {
            ListNode* nextTemp = curr->next;
            curr->next = prev;
            prev = curr;
            curr = nextTemp;
        }
        return prev;
    }
};
```
### Screenshot
<img width="968" height="555" alt="image" src="https://github.com/user-attachments/assets/4956e500-fba9-43d6-af0a-e318d51384a0" />
