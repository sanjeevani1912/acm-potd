# POTD Day 18 : Remove All Adjacent Duplicates In String

### Description
You are given a string `s` consisting of lowercase English letters. A duplicate removal consists of choosing two adjacent and equal letters and removing them. We repeatedly make duplicate removals until we no longer can. Return the final string.

### Approach
I used a **Stack-based** approach to solve this in linear time.
- I iterated through the string character by character.
- For each character, I checked if it matched the character at the top of the stack.
- If it matched, it meant I found an adjacent duplicate, so I popped the top element from the stack.
- If it didn't match (or if the stack was empty), I pushed the current character onto the stack.
- To optimize for space and avoid reversing the stack at the end, I used a `string` as a stack, using `push_back()` and `pop_back()` operations.



### Complexity
**Time: $O(n)$** — We traverse the string once, and each stack operation is $O(1)$.  
**Space: $O(n)$** — In the worst case (no duplicates), the result string/stack stores all $n$ characters.

### Code
```cpp
class Solution {
public:
    string removeDuplicates(string s) {
        string res = ""; // Using a string as a stack
        
        for (char c : s) {
            // If the stack is not empty and current char matches the top
            if (!res.empty() && res.back() == c) {
                res.pop_back(); // Remove the duplicate
            } else {
                res.push_back(c); // Add current char
            }
        }
        
        return res;
    }
};
```

### ScreenShot
<img width="1020" height="534" alt="image" src="https://github.com/user-attachments/assets/15f4011b-c996-4f24-a3a4-76c6efa2ea1e" />
