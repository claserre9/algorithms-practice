# DP Longest Common Subsequence

## Overview
The longest common subsequence (LCS) problem finds the longest sequence that appears in the same relative order in two strings. It's used in diff tools and bioinformatics sequence alignment.

## Detailed Explanation
A DP table `dp[i][j]` stores the length of the LCS of prefixes `a[:i]` and `b[:j]`. If characters match, `dp[i][j] = dp[i-1][j-1] + 1`; otherwise `max(dp[i-1][j], dp[i][j-1])`. Time complexity is O(n*m) and space O(n*m). Compared with naive exponential solutions, DP is efficient.

## Code Examples
### Python
```python
def lcs(a, b):
    n, m = len(a), len(b)
    dp = [[0]*(m+1) for _ in range(n+1)]
    for i in range(1, n+1):
        for j in range(1, m+1):
            if a[i-1] == b[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    return dp[n][m]
```

### PHP
```php
function lcs($a, $b) {
    $n = strlen($a); $m = strlen($b);
    $dp = array_fill(0, $n+1, array_fill(0, $m+1, 0));
    for ($i=1;$i<=$n;$i++) {
        for ($j=1;$j<=$m;$j++) {
            if ($a[$i-1] == $b[$j-1])
                $dp[$i][$j] = $dp[$i-1][$j-1] + 1;
            else
                $dp[$i][$j] = max($dp[$i-1][$j], $dp[$i][$j-1]);
        }
    }
    return $dp[$n][$m];
}
```

## Common Pitfalls & Warnings
- Mismanaging indices when filling the table.
- High memory usage for very long strings.

## Best Practices
- Use only two rows to save space when sequence strings are long.
- Reconstruct the subsequence by backtracking if needed.

## Mini Exercise or Challenge
Find the LCS length of `"abcde"` and `"ace"`.

## Solution
---
### Python
```python
print(lcs("abcde","ace"))  # 3
```
### PHP
```php
echo lcs("abcde","ace"); // 3
```
