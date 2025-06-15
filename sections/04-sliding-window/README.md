# Sliding Window

## Overview
The sliding window technique processes subsets of data using a window that moves across the array or string. It's useful for problems requiring sums, averages, or longest substrings. Common applications include network packet analysis and substring calculations.

## Detailed Explanation
A window of fixed or variable size slides across data, adding and removing elements as it goes. By keeping partial results, we avoid recomputing from scratch. Time complexity is often O(n) with O(1) additional space. Compared to naive approaches that re-evaluate every window, this saves significant time.

## Code Examples
### Python
```python
# max sum of k-length window
 def max_sum_window(arr, k):
     current = sum(arr[:k])
     best = current
     for i in range(k, len(arr)):
         current += arr[i] - arr[i - k]
         best = max(best, current)
     return best
```

### PHP
```php
function max_sum_window($arr, $k) {
    $current = array_sum(array_slice($arr, 0, $k));
    $best = $current;
    for ($i = $k; $i < count($arr); $i++) {
        $current += $arr[$i] - $arr[$i - $k];
        $best = max($best, $current);
    }
    return $best;
}
```

## Common Pitfalls & Warnings
- Overlooking initialization for the first window.
- Forgetting to update both ends when the window moves.

## Best Practices
- Use for problems requiring consecutive subsets.
- Choose window size carefully based on problem constraints.

## Mini Exercise or Challenge
Find the maximum sum of any 3 consecutive numbers in `[1,2,3,4,5]`.

## Solution
---
### Python
```python
print(max_sum_window([1,2,3,4,5], 3))  # Output: 12
```
### PHP
```php
echo max_sum_window([1,2,3,4,5], 3); // Output: 12
```
