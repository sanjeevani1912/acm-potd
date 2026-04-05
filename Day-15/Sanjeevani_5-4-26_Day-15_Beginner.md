# POTD Day 15 : Valid Parentheses

### Description
Given a string `s` containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid. A string is valid if open brackets are closed by the same type, in the correct order, and every closing bracket has a corresponding opening bracket.

### Approach
I used a **Stack-based** approach to solve this problem in linear time.
- I iterated through each character in the string.
- If the character was an opening bracket ('(', '{', or '['), I pushed it onto the stack.
- If the character was a closing bracket, I checked two things:
  1. Is the stack empty? (If so, there's no matching opening bracket, so it's invalid).
  2. Does the top of the stack match the current closing bracket? (If not, the order is incorrect).
- After processing the entire string, the stack must be empty for the string to be valid. This ensures every opening bracket was properly closed.



### Complexity
**Time: $O(n)$** — We traverse the string exactly once, and stack operations (push/pop) are $O(1)$.  
**Space: $O(n)$** — In the worst case (e.g., all opening brackets), we store all $n$ characters in the stack.

### Code
```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        
        for (char c : s) {
            // Push opening brackets to the stack
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);
            } 
            else {
                // If stack is empty or top doesn't match, it's invalid
                if (st.empty()) return false;
                
                char top = st.top();
                if ((c == ')' && top == '(') || 
                    (c == '}' && top == '{') || 
                    (c == ']' && top == '[')) {
                    st.pop();
                } else {
                    return false;
                }
            }
        }
        
        // Valid only if all brackets were matched and popped
        return st.empty();
    }
};
```

### Screenshot
<img width="1026" height="511" alt="image" src="https://github.com/user-attachments/assets/0521fc17-0ba3-4026-b932-bda8b2cbf0f6" />
