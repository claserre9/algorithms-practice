# DP Coin Change

## Overview
The coin change problem asks for the minimum number of coins needed to make a given amount from specific denominations. Dynamic programming avoids redundant calculations and is used in financial software and game design.

## Detailed Explanation
Create an array `dp` where `dp[i]` is the fewest coins to make amount `i`. Initialize `dp[0]=0` and others to infinity. For each coin, update `dp[i] = min(dp[i], dp[i-coin]+1)`. Complexity is O(n * amount) time and O(amount) space. Compared to greedy approaches, DP yields optimal solutions even when greedy fails.

## Code Examples
### Python
```python
def coin_change(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```

### PHP
```php
function coin_change($coins, $amount) {
    $dp = array_fill(0, $amount+1, INF);
    $dp[0] = 0;
    foreach ($coins as $coin) {
        for ($i=$coin;$i<=$amount;$i++) {
            $dp[$i] = min($dp[$i], $dp[$i-$coin]+1);
        }
    }
    return $dp[$amount] == INF ? -1 : $dp[$amount];
}
```

## Common Pitfalls & Warnings
- Forgetting to handle impossible amounts.
- Not iterating coins outermost may give suboptimal counts.

## Best Practices
- Iterate over coins first for unlimited supply.
- Use large value sentinel for impossible states.

## Mini Exercise or Challenge
Find minimum coins for amount `11` with coins `[1,2,5]`.

## Solution
---
### Python
```python
print(coin_change([1,2,5],11))  # 3
```
### PHP
```php
echo coin_change([1,2,5],11); // 3
```
