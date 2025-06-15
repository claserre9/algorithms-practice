# Backtracking

## Overview
Backtracking explores all possible configurations recursively, abandoning paths that violate constraints. It's common in puzzles like Sudoku, permutations, and constraint satisfaction problems.

## Detailed Explanation
The algorithm incrementally builds a candidate solution and abandons it as soon as it determines the path cannot possibly lead to a valid answer. Time complexity is often exponential because it explores many states, though pruning can help. Space complexity depends on recursion depth. Compared to brute force, backtracking prunes invalid paths earlier.

## Code Examples
### Python
```python
# generate permutations
 def permutations(nums, path=None):
     if path is None:
         path = []
     if not nums:
         return [path]
     result = []
     for i in range(len(nums)):
         result += permutations(nums[:i] + nums[i+1:], path + [nums[i]])
     return result
```

### PHP
```php
function permutations($nums, $path = []) {
    if (empty($nums)) return [$path];
    $result = [];
    for ($i = 0; $i < count($nums); $i++) {
        $rest = $nums;
        array_splice($rest, $i, 1);
        $result = array_merge($result, permutations($rest, array_merge($path, [$nums[$i]])));
    }
    return $result;
}
```

## Common Pitfalls & Warnings
- Not pruning paths leads to huge search spaces.
- Risk of stack overflow with deep recursion.

## Best Practices
- Add constraints early to prune invalid paths.
- Memoize or cache results when possible to avoid duplicates.

## Mini Exercise or Challenge
Use backtracking to generate all permutations of `[1,2]`.

## Solution
---
### Python
```python
print(permutations([1,2]))  # [[1,2],[2,1]]
```
### PHP
```php
print_r(permutations([1,2]));
```
