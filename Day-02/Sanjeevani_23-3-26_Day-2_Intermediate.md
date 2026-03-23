# POTD Day 2 : Subarray Sum Equals K

### Description
Given an array of integers `nums` and an integer `k`, return the total number of subarrays whose sum equals to `k`. A subarray is a contiguous non-empty sequence of elements within an array.

### Approach
I used the **Prefix Sum + Hash Map** approach to solve this in linear time.
- I maintained a running `currentSum` as I iterated through the array.
- For any index, if the `currentSum` is $S$, I check how many times a prefix sum of $S - k$ has occurred before using a hash map.
- If $S - (S - k) = k$, then the elements between those two points form a valid subarray.
- I initialized the map with `{0: 1}` to handle cases where the subarray starts from the very beginning of the array.

### Complexity
**Time: $O(n)$** — We traverse the array once, and hash map operations are $O(1)$ on average.  
**Space: $O(n)$** — In the worst case, we store all distinct prefix sums in the map.

### Code
```cpp
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        unordered_map<int, int> prevSum;
        prevSum[0] = 1; 
        
        int currentSum = 0;
        int count = 0;
        
        for (int i = 0; i < nums.size(); i++) {
            currentSum += nums[i];
            
            if (prevSum.find(currentSum - k) != prevSum.end()) {
                count += prevSum[currentSum - k];
            }
            
            prevSum[currentSum]++;
        }        
        return count;
    }
};

```
### Screenshot
<img width="966" height="538" alt="image" src="https://github.com/user-attachments/assets/16934b2b-a75c-4fd1-b4f4-1159341d2b6c" />
