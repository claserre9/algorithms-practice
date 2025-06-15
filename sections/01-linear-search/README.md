# Linear Search

## Overview
Linear search sequentially scans each element in a list until it finds the target value. It's simple but inefficient for large datasets. It's commonly used when the data isn't sorted or the dataset is small. Real-world uses include searching unsorted logs or quick lookups in short lists.

## Detailed Explanation
The algorithm starts at the first element and checks each item in order until the target is found or the list ends. Time complexity is O(n) because every element may be checked. Space complexity is O(1) since only a few variables are needed. When data is sorted, binary search is faster.

## Code Examples
### Python
```python
# basic version
 def linear_search(arr, target):
     for i, value in enumerate(arr):
         if value == target:
             return i
     return -1
```

```python
# slightly optimized version using while loop
 def linear_search_while(arr, target):
     i = 0
     while i < len(arr) and arr[i] != target:
         i += 1
     return i if i < len(arr) else -1
```

### PHP
```php
// basic version
function linear_search($arr, $target) {
    foreach ($arr as $i => $value) {
        if ($value == $target) {
            return $i;
        }
    }
    return -1;
}
```

```php
// optimized using while loop
function linear_search_while($arr, $target) {
    $i = 0;
    while ($i < count($arr) && $arr[$i] != $target) {
        $i++;
    }
    return $i < count($arr) ? $i : -1;
}
```

## Common Pitfalls & Warnings
- Assuming it is efficient for large datasets.
- Forgetting to handle not-found cases.

## Best Practices
- Use for small or unsorted data.
- Avoid when faster search structures are available.

## Mini Exercise or Challenge
Given `[5, 3, 2, 8, 1]` and target `8`, return the index using linear search.

## Solution
---
### Python
```python
arr = [5, 3, 2, 8, 1]
print(linear_search(arr, 8))  # Output: 3
```
### PHP
```php
$arr = [5, 3, 2, 8, 1];
echo linear_search($arr, 8); // Output: 3
```
