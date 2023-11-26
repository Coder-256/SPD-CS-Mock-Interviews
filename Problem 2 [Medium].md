# [Leetcode #55. Jump Game](https://leetcode.com/problems/jump-game/description/)

Python 3:

```py3
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        # Let's keep track of the farthest position we can currently reach, starting at 0
        n = len(nums)
        farthest_reach = 0
        for i in range(n):
            # First, let's check that we can reach position `i`; if not, give up.
            if farthest_reach < i:
                return False

            # Now, from position `i`, we can jump as far as `i+nums[i]`.
            # If that's farther than we could reach before, update `farthest_reach`
            if i+nums[i] > farthest_reach:
                farthest_reach = i+nums[i]

        return (farthest_reach >= n-1)
```

Java:

```java
class Solution {
    public boolean canJump(int[] nums) {
        // Let's keep track of the farthest position we can currently reach, starting at 0
        int n = nums.length;
        int farthestReach = 0;
        for (int i = 0; i < n; i++) {
            // First, let's check that we can reach position `i`; if not, give up.
            if (farthestReach < i)
                return false;

            // Now, from position `i`, we can jump as far as `i+nums[i]`.
            // If that's farther than we could reach before, update `farthestReach`
            if (i+nums[i] > farthestReach)
                farthestReach = i+nums[i];
        }

        return (farthestReach >= n-1);
    }
}
```

C++:

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        // Let's keep track of the farthest position we can currently reach, starting at 0
        int n = nums.size();
        int farthestReach = 0;
        for (int i = 0; i < n; i++) {
            // First, let's check that we can reach position `i`; if not, give up.
            if (farthestReach < i)
                return false;

            // Now, from position `i`, we can jump as far as `i+nums[i]`.
            // If that's farther than we could reach before, update `farthestReach`
            if (i+nums[i] > farthestReach)
                farthestReach = i+nums[i];
        }

        return (farthestReach >= n-1);
    }
};
```
