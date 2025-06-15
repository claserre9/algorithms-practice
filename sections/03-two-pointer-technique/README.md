# Two Pointer Technique

## Overview
The two pointer technique solves array problems by moving two indices toward each other or in tandem. It's effective for tasks like pair sums, sorting by parity, or reversing arrays. This approach appears in algorithm interviews and optimizes many O(n^2) solutions to O(n).

## Detailed Explanation
Typically one pointer starts at the beginning and the other at the end. Based on a condition, one or both pointers move closer until they meet. Complexity is usually O(n) time and O(1) space. It's more efficient than nested loops in problems like finding pairs with a given sum.

## Code Examples
### Python
```python
# example: check if array has two numbers that sum to target
 def has_pair_with_sum(arr, target):
     arr.sort()
     left, right = 0, len(arr) - 1
     while left < right:
         current = arr[left] + arr[right]
         if current == target:
             return True
         if current < target:
             left += 1
         else:
             right -= 1
     return False
```

### PHP
```php
function has_pair_with_sum($arr, $target) {
    sort($arr);
    $left = 0;
    $right = count($arr) - 1;
    while ($left < $right) {
        $current = $arr[$left] + $arr[$right];
        if ($current == $target) return true;
        if ($current < $target) {
            $left++;
        } else {
            $right--;
        }
    }
    return false;
}
```

## Common Pitfalls & Warnings
- Forgetting to sort when necessary.
- Moving the wrong pointer leading to infinite loops.

## Best Practices
- Use when you need linear time from originally quadratic solutions.
- Keep pointers well within array bounds.

## Mini Exercise or Challenge
Using the two pointer technique, determine if `[1,2,4,4]` has a pair that sums to `8`.

## Solution
---
### Python
```python
print(has_pair_with_sum([1,2,4,4], 8))  # True
```
### PHP
```php
echo has_pair_with_sum([1,2,4,4], 8) ? 'True' : 'False';
```
