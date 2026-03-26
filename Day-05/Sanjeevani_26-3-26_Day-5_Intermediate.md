# POTD Day 5 : Product of Array Except Self

### Description
Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`. The algorithm must run in $O(n)$ time and without using the division operation.

### Approach
I used the **Prefix and Suffix Products** approach to solve this in linear time without division.
- I initialized an `answer` array of the same size as `nums`.
- **First Pass (Prefix):** I iterated from left to right, storing the product of all elements to the left of each index `i` in `answer[i]`.
- **Second Pass (Suffix):** I iterated from right to left using a running product variable (`suffix_product`). I multiplied the existing value in `answer[i]` (which was the prefix product) by the `suffix_product`.
- This effectively calculates `Prefix[i-1] * Suffix[i+1]` for each index, giving the product of all elements except `nums[i]`.

### Complexity
**Time: $O(n)$** — We traverse the array twice (once for prefix, once for suffix).  
**Space: $O(1)$** — If we don't count the output array, we only use one extra variable for the suffix product.

### Code
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> answer(n, 1);
        
        // Calculate prefix products and store in answer array
        int prefix = 1;
        for (int i = 0; i < n; i++) {
            answer[i] = prefix;
            prefix *= nums[i];
        }
        
        // Calculate suffix products and multiply with current answer values
        int suffix = 1;
        for (int i = n - 1; i >= 0; i--) {
            answer[i] *= suffix;
            suffix *= nums[i];
        }
        
        return answer;
    }
};
```

### Screenshot
<img width="1070" height="545" alt="image" src="https://github.com/user-attachments/assets/2d8f1839-ed75-402d-9ae8-c5be2e9c333d" />
