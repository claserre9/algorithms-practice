# Floyd-Warshall Algorithm

## Overview
The Floyd-Warshall algorithm computes the shortest paths between all pairs of vertices in a weighted graph. It handles negative edges but not negative cycles and is used in routing and transitive closure problems.

## Detailed Explanation
The algorithm iteratively updates a distance matrix by considering each vertex as an intermediate node. Complexity is O(V^3) time and O(V^2) space. It's simpler than running Dijkstra from every vertex. Compared to Bellman-Ford, it's better for dense graphs requiring all-pairs distances.

## Code Examples
### Python
```python
def floyd_warshall(graph):
    dist = [row[:] for row in graph]
    n = len(dist)
    for k in range(n):
        for i in range(n):
            for j in range(n):
                if dist[i][k] + dist[k][j] < dist[i][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
    return dist
```

### PHP
```php
function floyd_warshall($graph) {
    $dist = $graph;
    $n = count($dist);
    for ($k=0;$k<$n;$k++) {
        for ($i=0;$i<$n;$i++) {
            for ($j=0;$j<$n;$j++) {
                if ($dist[$i][$k] + $dist[$k][$j] < $dist[$i][$j])
                    $dist[$i][$j] = $dist[$i][$k] + $dist[$k][$j];
            }
        }
    }
    return $dist;
}
```

## Common Pitfalls & Warnings
- High time complexity makes it impractical for large graphs.
- Forgetting to initialize unreachable distances with infinity.

## Best Practices
- Use for dense graphs or when all-pairs shortest paths are required.
- Avoid when only single-source paths are needed.

## Mini Exercise or Challenge
Find all-pairs shortest paths in matrix `[[0,3,INF],[2,0,INF],[INF,7,0]]`.

## Solution
---
### Python
```python
INF=float('inf')
matrix=[[0,3,INF],[2,0,INF],[INF,7,0]]
print(floyd_warshall(matrix))
```
### PHP
```php
$INF=INF;
$matrix=[[0,3,$INF],[2,0,$INF],[$INF,7,0]];
print_r(floyd_warshall($matrix));
```
