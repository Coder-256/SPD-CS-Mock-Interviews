# [LeetCode #982. Triples with Bitwise AND Equal To Zero](https://leetcode.com/problems/triples-with-bitwise-and-equal-to-zero/description/)

A brute-force `O(n^3)` solution, which is a good start but probably too slow:

```py3
class Solution:
    def countTriplets(self, nums: List[int]) -> int:
        answer = 0
        for x in nums:
            for y in nums:
                for z in nums:
                    if (x & y & z) == 0:
                        answer += 1
        return answer
```

This solution has some room for improvement.

---

The intuition you need here comes from looking carefully at the bounds (something that is often way too easy to forget!):

> - `1 <= nums.length <= 1000`
> - `0 <= nums[i] < 2^16`

A brute force solution probably leads to "Time Limit Exceeded", since `O(n^3)` would be ~1,000,000,000 iterations.

However, the numbers in this problem are all less than `2^16`. This means that each number will only use at most 15 bits, so there are only at most `2^15` = 32,768 possible AND triplets. That's a lot more manageable.

We can just count the number of AND "pairs", and then combine each pair with a third number to make a triplet, and count the number of triplets with a value of 0.

---

The following solution is `O(n^2 + 2^max(nums))`, which would be roughly ~100,000 + ~32,768 iterations, and focuses on readability over raw performance.

Python 3:

```py3
class Solution:
    def countTriplets(self, nums: List[int]) -> int:
        # Count the number of ways to make each "AND pair"
        pair_count = Counter()
        for x in nums:
            for y in nums:
                pair_count[x & y] += 1

        # Add each number to each "AND pair" to make an "AND triple"
        answer = 0
        for z in nums:
            for pair, count in pair_count.items():
                if (pair & z) == 0:
                    answer += count

        return answer
```

Java:

```java
class Solution {
    public int countTriplets(int[] nums) {
        // Count the number of ways to make each "AND pair"
        HashMap<Integer, Integer> pairCount = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums.length; j++) {
                int pair = nums[i] & nums[j];

                if (pairCount.containsKey(pair))
                    pairCount.put(pair, pairCount.get(pair)+1);
                else
                    pairCount.put(pair, 1);
            }
        }

        // Add each number to each "AND pair" to make an "AND triple"
        int answer = 0;
        for (int i = 0; i < nums.length; i++) {
            for (Map.Entry<Integer, Integer> entry : pairCount.entrySet()) {
                if ((nums[i] & entry.getKey()) == 0)
                    answer += entry.getValue();
            }
        }

        return answer;
    }
}
```

C++:

```cpp
class Solution {
public:
    int countTriplets(vector<int>& nums) {
        // Count the number of ways to make each "AND pair"
        unordered_map<int, int> pair_count;
        for (const auto& x : nums) {
            for (const auto& y : nums) {
                pair_count[x & y]++;
            }
        }

        // Add each number to each "AND pair" to make an "AND triple"
        int answer = 0;
        for (const auto& z : nums) {
            for (const auto& [pair, count] : pair_count) {
                if ((pair & z) == 0)
                    answer += count;
            }
        }

        return answer;
    }
};
```
