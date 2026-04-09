# POTD Day 19 : Backspace String Compare

### Description
Given two strings `s` and `t`, return `true` if they are equal when both are typed into empty text editors. The character '#' represents a backspace. Note that backspacing an empty text results in the text remaining empty.

### Approach
I used a **Stack-based** simulation to process both strings.
- I created a helper function to process a string into its final form.
- I iterated through the string:
  - If the character was not '#', I pushed it onto the stack (or string used as a stack).
  - If the character was '#' and the stack was not empty, I popped the last character.
- After processing both `s` and `t`, I compared the two resulting strings.
- This approach is intuitive as the "last-in" character is the "first" to be removed by a backspace, directly matching the LIFO property of a stack.

### Complexity
**Time: $O(n + m)$** — We traverse both strings `s` (length $n$) and `t` (length $m$) exactly once.  
**Space: $O(n + m)$** — In the worst case (no backspaces), we store the processed versions of both strings.

### Code
```cpp
class Solution {
public:
    bool backspaceCompare(string s, string t) {
        return build(s) == build(t);
    }
    
private:
    string build(string str) {
        string res = "";
        for (char c : str) {
            if (c != '#') {
                res.push_back(c);
            } else if (!res.empty()) {
                res.pop_back();
            }
        }
        return res;
    }
};
```

### Screenshot
<img width="842" height="547" alt="image" src="https://github.com/user-attachments/assets/bee2f974-4ad4-43c3-a882-209da888f40c" />
