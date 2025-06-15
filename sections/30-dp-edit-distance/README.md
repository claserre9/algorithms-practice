# DP Edit Distance

## Overview
Edit distance measures how many operations (insert, delete, replace) are required to transform one string into another. Dynamic programming provides an efficient algorithm used in spell checking and DNA analysis.

## Detailed Explanation
We build a matrix `dp[i][j]` representing the edit distance between prefixes `a[:i]` and `b[:j]`. Each cell takes the minimum of insertion, deletion, or substitution costs. Time complexity is O(n*m) and space O(n*m). Compared to naive recursion, DP is far faster.

## Code Examples
### Python
```python
def edit_distance(a, b):
    n, m = len(a), len(b)
    dp = [[0]*(m+1) for _ in range(n+1)]
    for i in range(n+1):
        dp[i][0] = i
    for j in range(m+1):
        dp[0][j] = j
    for i in range(1,n+1):
        for j in range(1,m+1):
            cost = 0 if a[i-1]==b[j-1] else 1
            dp[i][j] = min(dp[i-1][j]+1, dp[i][j-1]+1, dp[i-1][j-1]+cost)
    return dp[n][m]
```

### PHP
```php
function edit_distance($a, $b) {
    $n = strlen($a); $m = strlen($b);
    $dp = array_fill(0,$n+1,array_fill(0,$m+1,0));
    for ($i=0;$i<=$n;$i++) $dp[$i][0]=$i;
    for ($j=0;$j<=$m;$j++) $dp[0][$j]=$j;
    for ($i=1;$i<=$n;$i++) {
        for ($j=1;$j<=$m;$j++) {
            $cost = ($a[$i-1]==$b[$j-1]) ? 0 : 1;
            $dp[$i][$j] = min($dp[$i-1][$j]+1,$dp[$i][$j-1]+1,$dp[$i-1][$j-1]+$cost);
        }
    }
    return $dp[$n][$m];
}
```

## Common Pitfalls & Warnings
- Mixing up the indices leads to wrong values.
- High space usage for long strings.

## Best Practices
- Use row compression to reduce memory.
- Customize costs for different operations if needed.

## Mini Exercise or Challenge
Find edit distance between `"kitten"` and `"sitting"`.

## Solution
---
### Python
```python
print(edit_distance("kitten","sitting"))  # 3
```
### PHP
```php
echo edit_distance("kitten","sitting"); // 3
```
