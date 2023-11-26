# [LeetCode #2079. Watering Plants](https://leetcode.com/problems/watering-plants/description/)

Python 3:

```py3
class Solution:
    def wateringPlants(self, plants: List[int], capacity: int) -> int:
        n = len(plants)
        bucket = capacity  # How much water we have in our bucket
        steps = 0          # Number of steps we've taken so far
        for i in range(n):
            # Note: we begin each loop standing **right before** index `i`.
            # If we have enough water in our bucket to water the current plant:
            if bucket >= plants[i]:
                # Just take one step forward
                steps += 1
            else:
                # First we need to make a trip back to the river to refill the bucket
                # That'll take `i` steps back and `i+1` steps forward
                steps += i + (i+1)
                # Refill the bucket
                bucket = capacity

            # Pour out as much water as the plant needs
            bucket -= plants[i]

        return steps
```

Java:

```java
class Solution {
    public int wateringPlants(int[] plants, int capacity) {
        int n = plants.length;
        int bucket = capacity;  // How much water we have in our bucket
        int steps = 0;          // Number of steps we've taken so far
        for (int i = 0; i < n; i++) {
            // Note: we begin each loop standing **right before** index `i`.
            // If we have enough water in our bucket to water the current plant:
            if (bucket >= plants[i]) {
                // Just take one step forward
                steps++;
            } else {
                // First we need to make a trip back to the river to refill the bucket
                // That'll take `i` steps back and `i+1` steps forward
                steps += i + (i+1);
                // Refill the bucket
                bucket = capacity;
            }

            // Pour out as much water as the plant needs
            bucket -= plants[i];
        }

        return steps;
    }
}
```

C++:

```cpp
class Solution {
public:
    int wateringPlants(vector<int>& plants, int capacity) {
        int n = plants.size();
        int bucket = capacity;  // How much water we have in our bucket
        int steps = 0;          // Number of steps we've taken so far
        for (int i = 0; i < n; i++) {
            // Note: we begin each loop standing **right before** index `i`.
            // If we have enough water in our bucket to water the current plant:
            if (bucket >= plants[i]) {
                // Just take one step forward
                steps++;
            } else {
                // First we need to make a trip back to the river to refill the bucket
                // That'll take `i` steps back and `i+1` steps forward
                steps += i + (i+1);
                // Refill the bucket
                bucket = capacity;
            }

            // Pour out as much water as the plant needs
            bucket -= plants[i];
        }

        return steps;
    }
};
```
