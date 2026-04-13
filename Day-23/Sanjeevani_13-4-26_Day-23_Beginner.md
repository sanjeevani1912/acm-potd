# POTD Day 23 : Find the Town Judge

### Description
In a town of `n` people, a town judge exists if they trust nobody and everyone else trusts them. Given a `trust` array where `trust[i] = [a, b]` means person `a` trusts person `b`, return the label of the town judge if they exist, otherwise return -1.

### Approach
I used a **Single-Array Counting** approach (Degree Centrality) to solve this in linear time.
- I maintained an array `trustCount` of size `n + 1` to track the net "trust score" for each person.
- For every relationship `[a, b]` in the trust array:
  - Person `a` loses a point (`trustCount[a]--`) because the judge must trust nobody.
  - Person `b` gains a point (`trustCount[b]++`) because the judge must be trusted by everyone else.
- After processing all relationships, the town judge must have exactly `n - 1` points (meaning $n-1$ people trust them, and they trust 0 people).
- I then iterated through the people from 1 to `n` to find if anyone satisfies `trustCount[i] == n - 1`.

### Complexity
**Time: $O(N + T)$** — Where $N$ is the number of people and $T$ is the number of trust relationships. We traverse the trust array once and then the count array once.  
**Space: $O(N)$** — We use an array of size $N+1$ to store the trust scores.

### Code
```cpp
class Solution {
public:
    int findJudge(int n, vector<vector<int>>& trust) {
        // A judge must have (n-1) people trusting them and trust 0 people.
        // Net score = (number of people trusting them) - (number of people they trust)
        vector<int> trustCount(n + 1, 0);
        
        for (auto& relation : trust) {
            trustCount[relation[0]]--; // Person trusts someone
            trustCount[relation[1]]++; // Person is trusted by someone
        }
        
        for (int i = 1; i <= n; i++) {
            if (trustCount[i] == n - 1) {
                return i;
            }
        }
        
        return -1;
    }
};
```

### Screenshot

