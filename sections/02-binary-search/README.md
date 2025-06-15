# Binary Search

## Overview
Binary search efficiently locates a target value within a sorted array by repeatedly dividing the search interval in half. It is commonly used in libraries, databases, and anywhere sorted data is queried. Because it dramatically cuts down the number of comparisons, it's preferred over linear search for large sorted datasets.

## Detailed Explanation
The algorithm compares the target with the middle element. If equal, it returns the index. If the target is less, it searches the left half; otherwise, the right half. The process repeats until found or the interval is empty. Time complexity is O(log n), while space is O(1) for iterative or O(log n) for recursive implementations. Compared to linear search, binary search is much faster on sorted data.

## Code Examples
### Python
```python
# iterative version
 def binary_search(arr, target):
     low, high = 0, len(arr) - 1
     while low <= high:
         mid = (low + high) // 2
         if arr[mid] == target:
             return mid
         elif arr[mid] < target:
             low = mid + 1
         else:
             high = mid - 1
     return -1
```

```python
# recursive version
 def binary_search_rec(arr, target, low=0, high=None):
     if high is None:
         high = len(arr) - 1
     if low > high:
         return -1
     mid = (low + high) // 2
     if arr[mid] == target:
         return mid
     elif arr[mid] < target:
         return binary_search_rec(arr, target, mid + 1, high)
     else:
         return binary_search_rec(arr, target, low, mid - 1)
```

### PHP
```php
// iterative version
function binary_search($arr, $target) {
    $low = 0;
    $high = count($arr) - 1;
    while ($low <= $high) {
        $mid = intdiv($low + $high, 2);
        if ($arr[$mid] == $target) {
            return $mid;
        } elseif ($arr[$mid] < $target) {
            $low = $mid + 1;
        } else {
            $high = $mid - 1;
        }
    }
    return -1;
}
```

```php
// recursive version
function binary_search_rec($arr, $target, $low = 0, $high = null) {
    if ($high === null) {
        $high = count($arr) - 1;
    }
    if ($low > $high) return -1;
    $mid = intdiv($low + $high, 2);
    if ($arr[$mid] == $target) {
        return $mid;
    } elseif ($arr[$mid] < $target) {
        return binary_search_rec($arr, $target, $mid + 1, $high);
    } else {
        return binary_search_rec($arr, $target, $low, $mid - 1);
    }
}
```

## Common Pitfalls & Warnings
- Applying to unsorted data yields incorrect results.
- Midpoint calculation overflow in some languages (use safe formulas).

## Best Practices
- Ensure data is sorted before applying.
- Use iterative for constant space if recursion depth matters.

## Mini Exercise or Challenge
Use binary search to find `15` in `[1,4,7,9,12,15,19]`.

## Solution
---
### Python
```python
arr = [1,4,7,9,12,15,19]
print(binary_search(arr, 15))  # Output: 5
```
### PHP
```php
$arr = [1,4,7,9,12,15,19];
echo binary_search($arr, 15); // Output: 5
```
