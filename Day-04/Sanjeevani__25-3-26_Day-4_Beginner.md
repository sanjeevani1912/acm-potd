# POTD Day 4 : Missing Number

### Description
Given an array `nums` containing $n$ distinct numbers in the range $[0, n]$, return the only number in the range that is missing from the array.

### Approach
I used the **Sum Formula (Math)** approach to solve this in linear time and constant space.
- The sum of the first $n$ natural numbers is given by the formula: $Sum = \frac{n(n+1)}{2}$.
- I calculated the expected sum of all numbers from $0$ to $n$ using this formula.
- Then, I calculated the actual sum of all elements present in the `nums` array.
- The difference between the expected sum and the actual sum is the missing number.
- This approach is highly efficient as it only requires one pass through the array.

### Complexity
**Time: $O(n)$** — We traverse the array once to calculate the actual sum.  
**Space: $O(1)$** — We only use a few variables to store the sums regardless of the input size.

### Code
```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        // Calculate expected sum of [0, n]
        int expectedSum = n * (n + 1) / 2;
        
        // Calculate actual sum of elements in array
        int actualSum = 0;
        for (int num : nums) {
            actualSum += num;
        }
        
        // The difference is the missing number
        return expectedSum - actualSum;
    }
};
```
### Screenshot
<img width="896" height="546" alt="image" src="https://github.com/user-attachments/assets/5f16945d-68ad-490e-97d8-52abaa29a069" />
