# Insertion Sort

## Overview
Insertion sort builds the final sorted array one element at a time by comparing each new element with those before it. It's efficient for small or nearly sorted data and is often used in practice as a part of more complex algorithms.

## Detailed Explanation
We iterate over the array, inserting each item into its correct place among the previously sorted elements. In the worst case, it performs O(n^2) comparisons, but for nearly sorted data it approaches O(n). Space complexity is O(1). Compared to bubble sort, insertion sort tends to be faster because it makes fewer swaps.

## Code Examples
### Python
```python
# basic insertion sort
 def insertion_sort(arr):
     for i in range(1, len(arr)):
         key = arr[i]
         j = i - 1
         while j >= 0 and arr[j] > key:
             arr[j + 1] = arr[j]
             j -= 1
         arr[j + 1] = key
```

### PHP
```php
// basic insertion sort
function insertion_sort(&$arr) {
    for ($i = 1; $i < count($arr); $i++) {
        $key = $arr[$i];
        $j = $i - 1;
        while ($j >= 0 && $arr[$j] > $key) {
            $arr[$j + 1] = $arr[$j];
            $j--;
        }
        $arr[$j + 1] = $key;
    }
}
```

## Common Pitfalls & Warnings
- Not shifting elements correctly in the inner loop.
- Assuming it's efficient for large random arrays.

## Best Practices
- Use for small or mostly sorted datasets.
- Combine with faster sorts (e.g., in TimSort) for efficiency.

## Mini Exercise or Challenge
Sort `[5,2,4,6]` using insertion sort.

## Solution
---
### Python
```python
arr = [5,2,4,6]
insertion_sort(arr)
print(arr)  # [2,4,5,6]
```
### PHP
```php
$arr = [5,2,4,6];
insertion_sort($arr);
print_r($arr); // [2,4,5,6]
```
