# POTD Day 13 : Intersection of Two Linked Lists

### Description
Given the heads of two singly linked-lists `headA` and `headB`, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return `null`. The linked lists must retain their original structure after the function returns.

### Approach
I used the **Two-Pointer technique** to find the intersection point in $O(m + n)$ time and $O(1)$ space.
- I initialized two pointers, `ptrA` and `ptrB`, starting at the heads of the two lists.
- Both pointers traverse the lists node by node. 
- When `ptrA` reaches the end of list A, I redirect it to the head of list B. Similarly, when `ptrB` reaches the end of list B, I redirect it to the head of list A.
- By switching heads, both pointers will eventually travel the same total distance ($Length(A) + Length(B)$). 
- They are guaranteed to meet at the intersection node (if it exists) or at `NULL` (if no intersection exists) during the second pass.

### Complexity
**Time: $O(m + n)$** — In the worst case, each pointer traverses both lists once.  
**Space: $O(1)$** — No extra data structures are used; we only use two pointers.

### Code
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 * int val;
 * ListNode *next;
 * ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (headA == NULL || headB == NULL) return NULL;

        ListNode *ptrA = headA;
        ListNode *ptrB = headB;

        // Pointers will meet at the intersection point or at NULL
        while (ptrA != ptrB) {
            // If ptrA reaches the end, switch to headB; else move to next
            ptrA = (ptrA == NULL) ? headB : ptrA->next;
            // If ptrB reaches the end, switch to headA; else move to next
            ptrB = (ptrB == NULL) ? headA : ptrB->next;
        }

        return ptrA;
    }
};
```
### Screenshot
<img width="1035" height="539" alt="image" src="https://github.com/user-attachments/assets/7633b2eb-2401-4046-80d7-f5c28d1c4903" />
