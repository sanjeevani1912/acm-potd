# POTD Day 29 : Fibonacci Number

### Description
The Fibonacci numbers, commonly denoted F(n), form a sequence where each number is the sum of the two preceding ones, starting from 0 and 1. Given n, calculate F(n).

### Approach
I used an **Iterative Dynamic Programming** approach with **Space Optimization** to solve this in linear time.
- While the recursive formula F(n) = F(n-1) + F(n-2) is intuitive, a simple recursive solution would have a high time complexity of O(2^n) due to overlapping subproblems.
- Instead, I used two variables, `prev2` and `prev1`, to store the values of F(i-2) and F(i-1).
- Starting from i = 2 up to n, I calculated the current value as `curr = prev1 + prev2` and then shifted my pointers forward.
- This allows the calculation to happen in a single pass while only using constant extra space.

### Complexity
**Time: O(n)** — We traverse from 2 to n exactly once.  
**Space: O(1)** — We only store two previous values at any given time, regardless of how large n is.

### Code
```cpp
class Solution {
public:
    int fib(int n) {
        if (n <= 1) return n;
        
        int prev2 = 0; // F(0)
        int prev1 = 1; // F(1)
        int curr;
        
        for (int i = 2; i <= n; i++) {
            curr = prev1 + prev2;
            prev2 = prev1;
            prev1 = curr;
        }
        
        return prev1;
    }
};
```

### Screenshot
<img width="779" height="546" alt="image" src="https://github.com/user-attachments/assets/66a257ec-a0ad-4387-9063-ab18b299fb5f" />
