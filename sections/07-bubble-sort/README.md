# Bubble Sort

## Overview
Bubble sort repeatedly steps through the list, comparing adjacent elements and swapping them if they are in the wrong order. It's straightforward but inefficient, typically used for educational purposes or very small datasets.

## Detailed Explanation
Starting from the beginning of the list, compare adjacent pairs and swap them if needed. Each pass "bubbles" the largest remaining element to the end. Time complexity is O(n^2) in the average and worst case, and space complexity is O(1). Compared with more advanced sorts, bubble sort is slower but easy to implement.

## Code Examples
### Python
```python
# basic bubble sort
 def bubble_sort(arr):
     n = len(arr)
     for i in range(n):
         for j in range(0, n - i - 1):
             if arr[j] > arr[j + 1]:
                 arr[j], arr[j + 1] = arr[j + 1], arr[j]
```

```python
# optimized with early exit
 def bubble_sort_opt(arr):
     n = len(arr)
     for i in range(n):
         swapped = False
         for j in range(0, n - i - 1):
             if arr[j] > arr[j + 1]:
                 arr[j], arr[j + 1] = arr[j + 1], arr[j]
                 swapped = True
         if not swapped:
             break
```

### PHP
```php
// basic bubble sort
function bubble_sort(&$arr) {
    $n = count($arr);
    for ($i = 0; $i < $n; $i++) {
        for ($j = 0; $j < $n - $i - 1; $j++) {
            if ($arr[$j] > $arr[$j+1]) {
                $tmp = $arr[$j];
                $arr[$j] = $arr[$j+1];
                $arr[$j+1] = $tmp;
            }
        }
    }
}
```

```php
// optimized with early exit
function bubble_sort_opt(&$arr) {
    $n = count($arr);
    for ($i = 0; $i < $n; $i++) {
        $swapped = false;
        for ($j = 0; $j < $n - $i - 1; $j++) {
            if ($arr[$j] > $arr[$j+1]) {
                [$arr[$j], $arr[$j+1]] = [$arr[$j+1], $arr[$j]];
                $swapped = true;
            }
        }
        if (!$swapped) break;
    }
}
```

## Common Pitfalls & Warnings
- Using bubble sort on large datasets results in slow performance.
- Forgetting the inner loop range decreases each pass.

## Best Practices
- Reserve for teaching or tiny arrays.
- Replace with more efficient algorithms for production.

## Mini Exercise or Challenge
Sort `[3,1,4,2]` using bubble sort.

## Solution
---
### Python
```python
arr = [3,1,4,2]
bubble_sort(arr)
print(arr)  # [1,2,3,4]
```
### PHP
```php
$arr = [3,1,4,2];
bubble_sort($arr);
print_r($arr); // [1,2,3,4]
```
