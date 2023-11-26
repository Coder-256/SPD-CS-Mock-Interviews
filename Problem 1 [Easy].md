# [LeetCode #2148. Count Elements With Strictly Smaller and Greater Elements](https://leetcode.com/problems/count-elements-with-strictly-smaller-and-greater-elements/description/)

Python 3:

```py3
class Solution:
    def countElements(self, nums: List[int]) -> int:
        # First, find the smallest and largest values
        min_value = nums[0]
        max_value = nums[0]
        for x in nums:
            if x < min_value:
                min_value = x
            if x > max_value:
                max_value = x

        # Now, count the number of elements that are between the min and max value
        answer = 0
        for x in nums:
            if x > min_value and x < max_value:
                answer += 1

        return answer
```

Java:

```java
class Solution {
    public int countElements(int[] nums) {
        // First, find the smallest and largest values
        int minValue = nums[0];
        int maxValue = nums[0];
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] < minValue)
                minValue = nums[i];
            if (nums[i] > maxValue)
                maxValue = nums[i];
        }

        // Now, count the number of elements that are between the min and max value
        int answer = 0;
        for (int i = 0; i < nums.length; i++) {
            if ((nums[i] > minValue) && (nums[i] < maxValue))
                answer++;
        }

        return answer;
    }
}
```

C++:

```cpp
class Solution {
public:
    int countElements(vector<int>& nums) {
        // First, find the smallest and largest values
        int minValue = nums[0];
        int maxValue = nums[0];
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] < minValue)
                minValue = nums[i];
            if (nums[i] > maxValue)
                maxValue = nums[i];
        }

        // Now, count the number of elements that are between the min and max value
        int answer = 0;
        for (int i = 0; i < nums.size(); i++) {
            if ((nums[i] > minValue) && (nums[i] < maxValue))
                answer++;
        }

        return answer;
    }
};
```
