# POTD Day 2 : First Missing Positive

### Description
Given an unsorted integer array `nums`, return the smallest positive integer that is not present. The algorithm must run in $O(n)$ time and use $O(1)$ auxiliary space.

### Approach
I used the **Cyclic Sort (Index Mapping)** technique to solve this in-place.
- Since the array has length $n$, the first missing positive must be in the range $[1, n+1]$.
- I iterated through the array and tried to place every number `x` at its correct index `x - 1` (e.g., placing `1` at index `0`, `2` at index `1`).
- I only swapped numbers that were positive and within the range $[1, n]$.
- After rearranging, I performed a second pass to find the first index `i` where `nums[i] != i + 1`. The missing number is `i + 1`.
- If all numbers are in their correct positions, the missing number is `n + 1`.



### Complexity
**Time: $O(n)$** — Each element is visited or swapped at most a constant number of times.  
**Space: $O(1)$** — No extra data structures were used; the sorting was done in-place.

### Code
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n = nums.size();
        
        for (int i = 0; i < n; i++) {
            // While the current number is in range and not in its correct position
            while (nums[i] > 0 && nums[i] <= n && nums[nums[i] - 1] != nums[i]) {
                swap(nums[i], nums[nums[i] - 1]);
            }
        }
        
        // Find the first index where the number is not i + 1
        for (int i = 0; i < n; i++) {
            if (nums[i] != i + 1) {
                return i + 1;
            }
        }
        
        return n + 1;
    }
};

```
### Screenshot
<img width="1108" height="546" alt="image" src="https://github.com/user-attachments/assets/d1b00a71-420c-40fd-ac8f-e1544ce7c60d" />
