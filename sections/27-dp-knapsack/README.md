# DP Knapsack

## Overview
The 0/1 knapsack problem selects a subset of items with given weights and values to maximize value without exceeding capacity. Dynamic programming efficiently solves it by building solutions to smaller subproblems.

## Detailed Explanation
We use a table where `dp[i][w]` represents the maximum value achievable with the first `i` items and capacity `w`. Each item is either included or skipped. Complexity is O(nW) time and O(nW) space. Compared to brute force, DP avoids examining every subset.

## Code Examples
### Python
```python
def knapsack(values, weights, W):
    n = len(values)
    dp = [[0]*(W+1) for _ in range(n+1)]
    for i in range(1, n+1):
        for w in range(W+1):
            if weights[i-1] <= w:
                dp[i][w] = max(dp[i-1][w], dp[i-1][w-weights[i-1]] + values[i-1])
            else:
                dp[i][w] = dp[i-1][w]
    return dp[n][W]
```

### PHP
```php
function knapsack($values, $weights, $W) {
    $n = count($values);
    $dp = array_fill(0, $n+1, array_fill(0, $W+1, 0));
    for ($i=1;$i<=$n;$i++) {
        for ($w=0;$w<=$W;$w++) {
            if ($weights[$i-1] <= $w)
                $dp[$i][$w] = max($dp[$i-1][$w], $dp[$i-1][$w-$weights[$i-1]] + $values[$i-1]);
            else
                $dp[$i][$w] = $dp[$i-1][$w];
        }
    }
    return $dp[$n][$W];
}
```

## Common Pitfalls & Warnings
- Mixing up weight and value indices.
- Using recursion alone leads to exponential time.

## Best Practices
- Use bottom-up DP for clarity.
- Optimize space using a 1D array when possible.

## Mini Exercise or Challenge
Given values `[60,100,120]`, weights `[10,20,30]`, and `W=50`, compute max value.

## Solution
---
### Python
```python
print(knapsack([60,100,120],[10,20,30],50))  # 220
```
### PHP
```php
echo knapsack([60,100,120],[10,20,30],50); // 220
```
