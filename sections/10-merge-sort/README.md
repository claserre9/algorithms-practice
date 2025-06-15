# Merge Sort

## Overview
Merge sort is a divide and conquer algorithm that splits an array into halves, recursively sorts them, and then merges the results. It provides stable O(n log n) performance and is well-suited for large datasets.

## Detailed Explanation
The array is repeatedly divided until single-element arrays remain. These are merged back together in sorted order using a merge step that runs in linear time. Overall time complexity is O(n log n) and space complexity is O(n) due to additional arrays. Compared to quick sort, merge sort has consistent performance but requires more memory.

## Code Examples
### Python
```python
# merge sort implementation
 def merge_sort(arr):
     if len(arr) <= 1:
         return arr
     mid = len(arr) // 2
     left = merge_sort(arr[:mid])
     right = merge_sort(arr[mid:])
     return merge(left, right)

 def merge(left, right):
     result = []
     i = j = 0
     while i < len(left) and j < len(right):
         if left[i] < right[j]:
             result.append(left[i])
             i += 1
         else:
             result.append(right[j])
             j += 1
     result.extend(left[i:])
     result.extend(right[j:])
     return result
```

### PHP
```php
function merge_sort($arr) {
    if (count($arr) <= 1) return $arr;
    $mid = intdiv(count($arr), 2);
    $left = merge_sort(array_slice($arr, 0, $mid));
    $right = merge_sort(array_slice($arr, $mid));
    return merge_arrays($left, $right);
}

function merge_arrays($left, $right) {
    $result = [];
    $i = $j = 0;
    while ($i < count($left) && $j < count($right)) {
        if ($left[$i] < $right[$j]) {
            $result[] = $left[$i++];
        } else {
            $result[] = $right[$j++];
        }
    }
    return array_merge($result, array_slice($left, $i), array_slice($right, $j));
}
```

## Common Pitfalls & Warnings
- Forgetting to copy remaining elements when merging.
- High memory usage for large arrays.

## Best Practices
- Good choice when stable sort is required.
- Avoid when memory is constrained.

## Mini Exercise or Challenge
Sort `[8,3,5,1]` using merge sort.

## Solution
---
### Python
```python
print(merge_sort([8,3,5,1]))  # [1,3,5,8]
```
### PHP
```php
print_r(merge_sort([8,3,5,1]));
```
