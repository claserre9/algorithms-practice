# DP Fibonacci

## Overview
Computing Fibonacci numbers recursively results in exponential time due to repeated calculations. Dynamic programming uses memoization or bottom-up tables to compute them efficiently.

## Detailed Explanation
Memoization caches previous results to avoid duplication. Bottom-up tabulation fills an array from base cases up to n. Both achieve O(n) time with O(n) space. Compared to naive recursion's O(2^n) time, DP provides dramatic speedups.

## Code Examples
### Python
```python
# memoization
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
```

```python
# bottom-up
 def fib_bottom(n):
     if n <= 1:
         return n
     dp = [0,1]
     for i in range(2,n+1):
         dp.append(dp[i-1] + dp[i-2])
     return dp[n]
```

### PHP
```php
function fib($n, &$memo = []) {
    if ($n <= 1) return $n;
    if (isset($memo[$n])) return $memo[$n];
    $memo[$n] = fib($n-1,$memo) + fib($n-2,$memo);
    return $memo[$n];
}
```

```php
function fib_bottom($n) {
    if ($n <= 1) return $n;
    $dp = [0,1];
    for ($i=2;$i<=$n;$i++) $dp[$i] = $dp[$i-1] + $dp[$i-2];
    return $dp[$n];
}
```

## Common Pitfalls & Warnings
- Forgetting to memoize results in exponential slowdown.
- Overflow with large n if using fixed integer types.

## Best Practices
- Use bottom-up for iterative languages, memoization for clarity.
- Consider modulo operations for huge results.

## Mini Exercise or Challenge
Compute `fib(6)` using memoization.

## Solution
---
### Python
```python
print(fib(6))  # 8
```
### PHP
```php
echo fib(6); // 8
```
