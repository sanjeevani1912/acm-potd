# POTD Day 4 : Count of Smaller Numbers After Self

### Description
Given an integer array `nums`, return an integer array `counts` where `counts[i]` is the number of smaller elements to the right of `nums[i]`. 

### Approach
I used a **Modified Merge Sort** approach to solve this in $O(n \log n)$ time.
- I maintained an array of pairs, where each pair contains the value and its original index, to keep track of positions after sorting.
- During the merge step of the merge sort, when an element from the left subarray is moved into the merged array, I know exactly how many elements from the right subarray were already moved. 
- Since both subarrays are sorted, any element moved from the right subarray before an element from the left subarray is smaller than that left element.
- I incremented the count for the original index of the left element by the number of elements already taken from the right side.



### Complexity
**Time: $O(n \log n)$** — This is the standard complexity of merge sort, which is necessary to avoid TLE with $10^5$ elements.  
**Space: $O(n)$** — We use extra space for the temporary arrays and indices during the merge process.

### Code
```cpp
class Solution {
public:
    void merge(vector<pair<int, int>>& arr, int left, int mid, int right, vector<int>& count) {
        vector<pair<int, int>> temp(right - left + 1);
        int i = left;
        int j = mid + 1;
        int k = 0;
        int right_count = 0;

        while (i <= mid && j <= right) {
            if (arr[j].first < arr[i].first) {
                right_count++;
                temp[k++] = arr[j++];
            } else {
                count[arr[i].second] += right_count;
                temp[k++] = arr[i++];
            }
        }

        while (i <= mid) {
            count[arr[i].second] += right_count;
            temp[k++] = arr[i++];
        }

        while (j <= right) {
            temp[k++] = arr[j++];
        }

        for (int p = 0; p < temp.size(); p++) {
            arr[left + p] = temp[p];
        }
    }

    void mergeSort(vector<pair<int, int>>& arr, int left, int right, vector<int>& count) {
        if (left >= right) return;
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid, count);
        mergeSort(arr, mid + 1, right, count);
        merge(arr, left, mid, right, count);
    }

    vector<int> countSmaller(vector<int>& nums) {
        int n = nums.size();
        vector<int> count(n, 0);
        vector<pair<int, int>> arr;
        for (int i = 0; i < n; i++) {
            arr.push_back({nums[i], i});
        }

        mergeSort(arr, 0, n - 1, count);
        return count;
    }
};
```
### Screenshot
<img width="1186" height="541" alt="image" src="https://github.com/user-attachments/assets/181dbdf7-8d88-46d9-aca6-2c17950dbb35" />
