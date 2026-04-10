# POTD Day 20 : Remove Outermost Parentheses

### Description
Given a valid parentheses string `s`, consider its primitive decomposition $s = P_1 + P_2 + ... + P_k$. A primitive string is a non-empty valid parentheses string that cannot be split further. Return `s` after removing the outermost parentheses of every primitive string in its decomposition.

### Approach
I used a **Balance Counting** approach to identify and strip the outermost parentheses without needing an explicit stack.
- I maintained an `opened` counter to track the nesting level of the parentheses.
- I iterated through each character `c` in the string:
  - If `c` is an opening bracket `'('`:
    - If `opened > 0`, it means this bracket is *not* the outermost one of a primitive group, so I added it to the result.
    - I then incremented the `opened` count.
  - If `c` is a closing bracket `')'`:
    - If `opened > 1`, it means this bracket is *not* the outermost one of a primitive group, so I added it to the result.
    - I then decremented the `opened` count.
- This logic effectively skips the first `'('` (where `opened` is 0) and the last `')'` (where `opened` is 1) of every primitive part.

### Complexity
**Time: $O(n)$** — We traverse the string once, performing constant-time operations for each character.  
**Space: $O(n)$** — The space is used to store the resulting string. No extra auxiliary data structures were used.

### Code
```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
        string res = "";
        int opened = 0;
        
        for (char c : s) {
            if (c == '(') {
                // If it's not the first bracket of a primitive string, add it
                if (opened > 0) res += c;
                opened++;
            } else {
                // If it's not the last bracket of a primitive string, add it
                if (opened > 1) res += c;
                opened--;
            }
        }
        
        return res;
    }
};
```

### Screenshot
<img width="871" height="543" alt="image" src="https://github.com/user-attachments/assets/25b7f68e-8807-41ce-8b8c-9c808c8a0c8d" />
