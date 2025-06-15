# Quick Sort

## Overview
Quick sort sorts an array by partitioning it around a pivot element, recursively sorting the partitions. It's widely used because of its average O(n log n) performance and in-place nature.

## Detailed Explanation
Choose a pivot and partition elements into those less than the pivot and those greater. Recursively sort each partition. Average time complexity is O(n log n), but worst case is O(n^2) when poorly balanced. Space complexity is O(log n) for recursion. Compared to merge sort, quick sort uses less memory but can degrade with bad pivot choices.

## Code Examples
### Python
```python
# simple quick sort
 def quick_sort(arr):
     if len(arr) <= 1:
         return arr
     pivot = arr[len(arr) // 2]
     left = [x for x in arr if x < pivot]
     middle = [x for x in arr if x == pivot]
     right = [x for x in arr if x > pivot]
     return quick_sort(left) + middle + quick_sort(right)
```

```python
# in-place partition quicksort
 def quick_sort_inplace(arr, low=0, high=None):
     if high is None:
         high = len(arr) - 1
     if low < high:
         p = partition(arr, low, high)
         quick_sort_inplace(arr, low, p - 1)
         quick_sort_inplace(arr, p + 1, high)

 def partition(arr, low, high):
     pivot = arr[high]
     i = low
     for j in range(low, high):
         if arr[j] <= pivot:
             arr[i], arr[j] = arr[j], arr[i]
             i += 1
     arr[i], arr[high] = arr[high], arr[i]
     return i
```

### PHP
```php
function quick_sort($arr) {
    if (count($arr) <= 1) return $arr;
    $pivot = $arr[intdiv(count($arr), 2)];
    $left = $right = $middle = [];
    foreach ($arr as $v) {
        if ($v < $pivot) $left[] = $v;
        elseif ($v > $pivot) $right[] = $v;
        else $middle[] = $v;
    }
    return array_merge(quick_sort($left), $middle, quick_sort($right));
}
```

```php
function quick_sort_inplace(&$arr, $low = 0, $high = null) {
    if ($high === null) $high = count($arr) - 1;
    if ($low < $high) {
        $p = partition($arr, $low, $high);
        quick_sort_inplace($arr, $low, $p - 1);
        quick_sort_inplace($arr, $p + 1, $high);
    }
}

function partition(&$arr, $low, $high) {
    $pivot = $arr[$high];
    $i = $low;
    for ($j = $low; $j < $high; $j++) {
        if ($arr[$j] <= $pivot) {
            [$arr[$i], $arr[$j]] = [$arr[$j], $arr[$i]];
            $i++;
        }
    }
    [$arr[$i], $arr[$high]] = [$arr[$high], $arr[$i]];
    return $i;
}
```

## Common Pitfalls & Warnings
- Choosing bad pivots leads to worst-case performance.
- In-place version requires careful index management.

## Best Practices
- Randomize or median-of-three pivot selection.
- Prefer iterative stack-based versions for very large arrays.

## Mini Exercise or Challenge
Sort `[9,3,7,1]` using quick sort.

## Solution
---
### Python
```python
print(quick_sort([9,3,7,1]))  # [1,3,7,9]
```
### PHP
```php
print_r(quick_sort([9,3,7,1]));
```
