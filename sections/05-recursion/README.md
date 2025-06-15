# Recursion

## Overview
Recursion is a programming technique where a function calls itself with smaller inputs until reaching a base case. It's widely used to solve problems that can be divided into similar subproblems such as tree traversal or factorial computation.

## Detailed Explanation
Each recursive call reduces the problem size, eventually hitting the base case where no further calls are made. Recursion can lead to elegant solutions but must be carefully designed to prevent infinite loops. Time and space complexities depend on the problem—usually O(n) time and O(n) space due to call stack. Iterative approaches may offer better space usage in some scenarios.

## Code Examples
### Python
```python
# factorial using recursion
 def factorial(n):
     if n == 0:
         return 1
     return n * factorial(n - 1)
```

```python
# tail recursion example (Python doesn't optimize tail calls)
 def factorial_tail(n, acc=1):
     if n == 0:
         return acc
     return factorial_tail(n - 1, acc * n)
```

### PHP
```php
// factorial using recursion
function factorial($n) {
    if ($n == 0) return 1;
    return $n * factorial($n - 1);
}
```

```php
// tail recursion style
function factorial_tail($n, $acc = 1) {
    if ($n == 0) return $acc;
    return factorial_tail($n - 1, $acc * $n);
}
```

## Common Pitfalls & Warnings
- Missing or incorrect base case causing infinite recursion.
- Stack overflow when recursion depth is large.

## Best Practices
- Ensure each call moves toward the base case.
- Prefer iteration when deep recursion may exceed stack limits.

## Mini Exercise or Challenge
Write a recursive function to compute the sum of an array `[1,2,3]`.

## Solution
---
### Python
```python
def sum_array(arr):
    if not arr:
        return 0
    return arr[0] + sum_array(arr[1:])
print(sum_array([1,2,3]))  # Output: 6
```
### PHP
```php
function sum_array($arr) {
    if (empty($arr)) return 0;
    $head = array_shift($arr);
    return $head + sum_array($arr);
}

echo sum_array([1,2,3]); // Output: 6
```
