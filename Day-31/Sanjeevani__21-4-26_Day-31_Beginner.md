# POTD Day 31 : Climbing Stairs

### Description
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

### Approach
I used an **Iterative Dynamic Programming** approach to solve this problem efficiently.
- To reach step `n`, you must have come from either step `n-1` (by taking a 1-step jump) or step `n-2` (by taking a 2-step jump).
- Therefore, the number of ways to reach step `n` is the sum of the ways to reach `n-1` and `n-2`.
- This follows the **Fibonacci sequence** pattern.
- I optimized the space complexity by using only two variables, `prev1` and `prev2`, to store the results of the two previous steps, rather than an entire array.



### Complexity
**Time: $O(n)$** — We iterate from step 3 up to `n` exactly once.  
**Space: $O(1)$** — We only store the count of ways for the two previous steps.

### Code
```cpp
class Solution {
public:
    int climbStairs(int n) {
        // Base cases
        if (n <= 2) return n;
        
        int prev2 = 1; // Ways to reach step 1
        int prev1 = 2; // Ways to reach step 2
        int current = 0;
        
        for (int i = 3; i <= n; i++) {
            current = prev1 + prev2;
            prev2 = prev1;
            prev1 = current;
        }
        
        return prev1;
    }
};
```

### Screenshot
<img width="949" height="536" alt="image" src="https://github.com/user-attachments/assets/68b52643-fea0-402e-bcfb-47c3e77b7e9e" />
