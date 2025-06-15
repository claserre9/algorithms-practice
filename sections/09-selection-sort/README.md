# Selection Sort

## Overview
Selection sort repeatedly selects the minimum element from the unsorted portion and places it at the beginning. It's conceptually simple but inefficient on large lists.

## Detailed Explanation
For each position, find the minimum in the remaining array and swap it into place. This requires O(n^2) comparisons and O(1) space. Compared to insertion sort, selection sort makes fewer swaps but still scans the entire list every pass.

## Code Examples
### Python
```python
# basic selection sort
 def selection_sort(arr):
     n = len(arr)
     for i in range(n):
         min_idx = i
         for j in range(i+1, n):
             if arr[j] < arr[min_idx]:
                 min_idx = j
         arr[i], arr[min_idx] = arr[min_idx], arr[i]
```

### PHP
```php
function selection_sort(&$arr) {
    $n = count($arr);
    for ($i = 0; $i < $n; $i++) {
        $min = $i;
        for ($j = $i + 1; $j < $n; $j++) {
            if ($arr[$j] < $arr[$min]) {
                $min = $j;
            }
        }
        [$arr[$i], $arr[$min]] = [$arr[$min], $arr[$i]];
    }
}
```

## Common Pitfalls & Warnings
- Not updating the minimum index correctly.
- Expecting good performance on large datasets.

## Best Practices
- Rarely used in production but useful for teaching.
- Works well when memory writes are costly.

## Mini Exercise or Challenge
Sort `[4,3,1,2]` using selection sort.

## Solution
---
### Python
```python
arr = [4,3,1,2]
selection_sort(arr)
print(arr)  # [1,2,3,4]
```
### PHP
```php
$arr = [4,3,1,2];
selection_sort($arr);
print_r($arr); // [1,2,3,4]
```
